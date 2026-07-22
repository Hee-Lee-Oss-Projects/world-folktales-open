# TASKS — world-folktales-open

> Status: Draft · Version: 0.1.0 · Last updated: 2026-06-28 · Owner: TBD (maintainer) · Lane: donated

Itemized backlog for the open, multilingual, dual-gated folktale commons. See [`PLAN.md`](./PLAN.md)
for context, the two gates (copyright + cultural), and the roadmap (M0–M3).

## How these tasks map to Hee-Lee Oss

Each task below becomes a Hee-Lee Oss **Task JSON** validated against `packages/schema/src/schemas.ts`.
Field mapping:

- **id** — stable `world-folktales-open-<area>-NNN` (the table ID).
- **title** — the table Title.
- **project** — `world-folktales-open`.
- **type** — one of `code | research | writing | data | design-spec | maintenance` (table "Type").
- **lane** — `donated` for all tasks here. Any future metered run would be `funded` and must add
  `fundedBudgetUsd`.
- **priority** — `high | medium | low`.
- **domain** — e.g. `["culture","folklore","open-content","education","translation","heritage"]`.
- **riskTier** — `low | medium | high`. Collection/scaffolding/docs are **low**; translations,
  retellings, and any living-tradition/Indigenous material are **medium** (accuracy + cultural review).
  No `high` (no medical/legal/safety content).
- **urgent** — boolean (default `false`).
- **deliverable** — `pr | dataset | document | translation` (table "Deliverable").
- **tokenEstimate** — `small | medium | large` (table "Size").
- **status** — `open | in-progress | review | delivered | done` (start `open`).
- **context / objective / acceptanceCriteria[] / resources[] / output** — per task.
- **requestor** — `jdev1977` / beneficiary class until a named partner is secured.
- **verifiedNeed** — **`false`** while no committed partner/steward is secured (honest; the *gap* is
  real but the last-mile beneficiary is TO BE SECURED).
- **outputLicense** — `MIT` (code), `CC0-1.0` (verbatim PD-derived content/docs), `CC-BY-4.0` (new
  translations/retellings), or `CC-BY-SA-4.0` (where CC BY-SA source material is incorporated).

> **Standing guardrails on every collection/translation/retelling task:**
> 1. No source may be touched until its `sources/allowlist.yml` entry is **copyright-`approved`** by the
>    copyright reviewer. Reusing any copyrighted translation/anthology/retelling is **refused and
>    flagged** — out of scope, full stop.
> 2. No living-tradition / Indigenous tale may be published until it **passes cultural review**;
>    sacred/secret/restricted material is **excluded and flagged** regardless of copyright status
>    (copyright PD ≠ cultural permission). When in doubt, exclude and flag.
> 3. No tale ships without a **resolvable source-edition citation** and a **cultural attribution**
>    (`origin: uncertain` is an allowed honest value; a guessed origin is not). No AI-fabricated tales.

---

## Milestone M0 — Foundation & dual-gate spine

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| world-folktales-open-schema-001 | Define tale schema (provenance, cultural attribution, ATU/motif, language, reading level, warnings) | design-spec | small | low | document | — | Maintainer + cultural reviewer |
| world-folktales-open-license-001 | Source allow-list schema + per-edition copyright-gate policy | design-spec | small | medium | document | — | Copyright reviewer |
| world-folktales-open-culture-001 | Cultural-attribution & sensitivity policy (general vs. living-tradition; sacred-exclusion; TK/CARE; PD≠cultural-open) | design-spec | small | medium | document | — | Cultural reviewer |
| world-folktales-open-license-002 | Analyze & record first 3 candidate source editions (≥1 copyright-approved) | research | medium | medium | document | world-folktales-open-license-001 | Copyright reviewer |
| world-folktales-open-id-001 | Commit host-independent persistent-ID namespace (w3id/PURL) | design-spec | small | low | document | world-folktales-open-schema-001 | Maintainer |
| world-folktales-open-ci-001 | CI scaffold: JSON-Schema + provenance + attribution linters | code | medium | low | pr | world-folktales-open-schema-001 | Maintainer |
| world-folktales-open-partner-001 | Steward + originating-community outreach (status logged) | research | small | low | document | — | Maintainer |

**Acceptance criteria (key M0 tasks)**

- **world-folktales-open-schema-001**
  - Schema defines per-tale fields: id, title(s), culture/region/country, `atuType`, `motifs[]`,
    `language` (BCP-47), `artifactType` (collected/translated/retold), full `source` block with rights
    basis, `translationProvenance`/`retellingNote`, `culturalAttribution` block, `contentWarnings[]`,
    `readingLevel`/`ageRange`, `license`, `provenanceChain`.
  - `origin: uncertain` is a permitted, honest value; no field allows a guessed value.
  - Published as a human-readable spec plus a machine artifact (`schema/tale.schema.json`).
- **world-folktales-open-license-001**
  - `sources/allowlist.yml` schema records: title, author/collector, translator, edition year,
    publisher, host, URL, format, rights basis, **per-copy/edition rights analysis**, verifier, and
    `status: approved|rejected|pending`.
  - Policy states the "tale is old ⇒ free" fallacy is invalid; the **specific translation/edition**
    must be PD/open. Anti-laundering controls documented (edition/page-level citation; contributor
    attestation; reviewer spot-checks for modern phrasing).
- **world-folktales-open-culture-001**
  - Classifies tales as **general/literary** vs. **living-tradition/Indigenous**, with different review
    paths.
  - States explicitly that **copyright PD ≠ cultural permission**; sacred/secret/restricted material is
    excluded; uncertainty defaults to exclude-and-flag.
  - References TK Labels/Notices (Local Contexts) and CARE Principles; defines the
    community-open-evidence / consent bases for living-tradition material.
- **world-folktales-open-ci-001**
  - CI fails on any tale lacking a resolvable source-edition citation.
  - CI fails on any tale lacking a cultural attribution.
  - CI rejects any tale referencing a source not `approved` in the allow-list; validates against
    `tale.schema.json`.

**M0 Definition of Done:** tale schema v0 published; allow-list schema + copyright policy merged with
≥3 editions analyzed and ≥1 approved; cultural-attribution & sensitivity policy published; persistent-ID
namespace committed; CI schema/provenance/attribution gates live; partner + community outreach
initiated with status logged; **a qualified copyright reviewer named (hard exit; if the seat is empty
M0 cannot exit — escalate per PLAN.md fallback)**. `pnpm build && pnpm test && pnpm lint` green.

---

## Milestone M1 — First sourced slice (proof of pipeline)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| world-folktales-open-collect-001 | Build assistive transcription/OCR-correction pipeline (flag-on-doubt) | code | medium | low | pr | world-folktales-open-ci-001, world-folktales-open-license-002 | Maintainer |
| world-folktales-open-data-001 | Collect ≥25 verbatim PD tales from approved English-language editions | data | large | low | dataset | world-folktales-open-collect-001 | Copyright reviewer |
| world-folktales-open-atu-001 | ATU-type + motif classification for the M1 slice | research | small | low | dataset | world-folktales-open-data-001 | Maintainer |
| world-folktales-open-culture-002 | Cultural review of any living-tradition items in the M1 slice | research | small | medium | document | world-folktales-open-data-001, world-folktales-open-culture-001 | Cultural reviewer |
| world-folktales-open-export-001 | JSON + JSON-LD export tooling under the persistent-ID namespace | code | medium | low | pr | world-folktales-open-data-001 | Maintainer |
| world-folktales-open-partner-002 | Identify & engage ≥1 candidate steward for adoption | research | small | low | document | world-folktales-open-partner-001 | Maintainer |

**Acceptance criteria (key M1 tasks)**

- **world-folktales-open-data-001**
  - ≥25 verbatim PD tales published, each with an **edition/page-level** source citation and a recorded
    rights basis for the *specific edition/translation* used.
  - Each tale carries a cultural attribution (`origin: uncertain` allowed and recorded honestly).
  - Each tale has an ATU type (or `unclassified` with rationale) and language tag.
  - **100%** pass CI (schema + provenance + attribution + allow-list) before review.
  - OCR (if used) is on PD machine-print only and human-corrected against the source image; ambiguous
    text is flagged, never guessed.
- **world-folktales-open-culture-002**
  - Every living-tradition/Indigenous item in the slice is reviewed; sacred/restricted items are
    excluded and flagged with a recorded rationale.
  - Attribution accuracy confirmed; TK context attached where applicable.
  - No living-tradition item is published before this review passes (a **named cultural reviewer** must
    exist first).
- **world-folktales-open-export-001**
  - Produces valid JSON and JSON-LD with stable persistent IDs.
  - Export round-trips (re-import validates against `tale.schema.json`); licence + attribution metadata
    included per tale.

**M1 entry precondition (hard gate):** every source edition used is recorded in `allowlist.yml` as
copyright-`approved` before transcription; a cultural reviewer is named before any living-tradition tale
is published.

**M1 Definition of Done:** ≥25 verbatim PD tales published with 100% provenance + attribution; any
living-tradition items cultural-reviewed (or excluded+flagged); ATU classification applied; JSON +
JSON-LD exports under the persistent-ID namespace; ≥1 candidate steward in conversation.

---

## Milestone M2 — Multilingual, retellings & reader

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| world-folktales-open-translate-001 | Produce ≥20 new CC-BY translations (multi-language) with review | writing | large | medium | translation | world-folktales-open-data-001, world-folktales-open-culture-001 | Language + cultural reviewers |
| world-folktales-open-retell-001 | Produce ≥10 child-friendly retellings with change notes + review | writing | medium | medium | document | world-folktales-open-data-001, world-folktales-open-culture-001 | Cultural + language reviewers |
| world-folktales-open-readlevel-001 | Add reading-level/age + content-warning metadata (≥80% of tales) | data | small | low | dataset | world-folktales-open-data-001 | Maintainer |
| world-folktales-open-reader-001 | Static reader/explorer over JSON (no accounts/PII) | code | medium | low | pr | world-folktales-open-export-001 | Maintainer |
| world-folktales-open-docs-001 | Data dictionary + usage/attribution/citation guide for consumers | writing | small | low | document | world-folktales-open-reader-001 | Maintainer |
| world-folktales-open-metrics-001 | Reuse-metrics tracking (downloads / ingests) | maintenance | small | low | document | world-folktales-open-reader-001 | Maintainer |

**Acceptance criteria (key M2 tasks)**

- **world-folktales-open-translate-001**
  - ≥20 new translations across multiple target languages, each pointing to its PD base tale and
    carrying `translationProvenance` (translator + reviewer).
  - Each passes a language-fluent **back-check** against the source for meaning and register; ≥95% of
    the sampled audit verifies.
  - Living-tradition source tales' translations also pass cultural review. Output licence `CC-BY-4.0`.
- **world-folktales-open-retell-001**
  - Each retelling records a **change note** (what was simplified and why) and its base tale id.
  - Each passes cultural review for preserved meaning (no distortion) and accuracy review.
  - Reading level/age range set; content warnings applied. Output licence `CC-BY-4.0`.
- **world-folktales-open-reader-001**
  - Browse a tale and see its text, source citation, cultural attribution, ATU type, language, and
    licence; filter by language/region/reading level.
  - Static / no-account; collects no visitor PII; links to raw exports and to each source.

**M2 Definition of Done:** ≥30 new translations/retellings published with language + cultural + accuracy
review and retelling change notes; ≥10 languages with ≥1 complete tale; reading-level/warnings on ≥80%
of tales; static reader + documented exports live; reuse metrics tracked.

---

## Milestone M3 — Scale & steward adoption (shipped)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| world-folktales-open-data-002 | Scale to ≥300 tales across ≥25 regions / ≥10 languages | data | large | medium | dataset | world-folktales-open-translate-001, world-folktales-open-culture-002 | Copyright + cultural reviewers |
| world-folktales-open-audit-001 | Stratified copyright + accuracy audit of a release (sampling frame) | research | small | medium | document | world-folktales-open-data-002 | Copyright + language reviewers |
| world-folktales-open-partner-003 | Secure steward adoption + ≥1 documented citation/use | research | medium | low | document | world-folktales-open-partner-002 | Maintainer |
| world-folktales-open-sustain-001 | Sustainability, hosting + reviewer-rotation/throughput plan | writing | small | low | document | world-folktales-open-partner-003 | Maintainer |

**Acceptance criteria (key M3 tasks)**

- **world-folktales-open-data-002**
  - ≥300 tales across ≥25 regions and ≥10 languages; each new source passed the copyright gate before
    collection; 100% provenance + attribution maintained.
  - All living-tradition items cultural-reviewed; sacred/restricted excluded+flagged.
- **world-folktales-open-audit-001**
  - Stratified sample (min 50 or whole release; strata by rights basis and cultural category;
    independent auditor) audited.
  - Copyright pass rate 100% on the sample (any failure ⇒ recall-and-fix); translation/retelling
    accuracy ≥95%.
- **world-folktales-open-partner-003**
  - A named steward (library / folklore society / heritage org / language community) commits to
    adopt/host and cite the corpus; ≥1 concrete citation or downstream use documented.

**M3 Definition of Done (project "shipped"):** ≥300 tales across ≥25 regions / ≥10 languages; 100%
provenance + attribution; all living-tradition items cultural-reviewed; copyright audit 100% and
accuracy ≥95% on the sampled frame; ≥1 steward has adopted/cited the corpus; sustainability plan in
effect.

---

## Backlog / future (sized, unscheduled)

| ID | Title | Type | Size | Risk | Deliverable | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| world-folktales-open-variants-001 | Cross-culture variant linking by ATU type | data | medium | low | dataset | Links variants without crowning a "real" version |
| world-folktales-open-epub-001 | EPUB/PDF reading-pack export for educators | code | medium | low | pr | Print/offline use; per-tale licence carried |
| world-folktales-open-consent-001 | Community-contribution + consent workflow for living-tradition tales | design-spec | medium | medium | document | Needs originating-community partners |
| world-folktales-open-translate-002 | Translation packs for additional low-resource languages | writing | large | medium | translation | Driven by language-community partners |
| world-folktales-open-quality-001 | Automated anomaly/duplication flagging for review | code | medium | low | pr | Assistive QA, human-confirmed |
| world-folktales-open-i18n-001 | Multilingual UI labels for the reader (Wikidata CC0) | data | small | low | dataset | No content rights impact |

---

## Example task JSON

Schema-valid Task JSON for the first M0 task (`world-folktales-open-schema-001`):

```json
{
  "id": "world-folktales-open-schema-001",
  "title": "Define tale schema (provenance, cultural attribution, ATU/motif, language, reading level, warnings)",
  "project": "world-folktales-open",
  "type": "design-spec",
  "lane": "donated",
  "priority": "high",
  "domain": ["culture", "folklore", "open-content", "education", "heritage"],
  "riskTier": "low",
  "urgent": false,
  "deliverable": "document",
  "tokenEstimate": "small",
  "status": "open",
  "context": "An open, multilingual folktale commons needs a shared tale schema before any content is ingested. Every tale must carry two things: a verifiable copyright provenance (the specific PD/open source edition, not just the ancient tale) and a cultural attribution (origin tradition; sacred/restricted material excluded). Copyright public-domain status is NOT cultural permission. Sources are public-domain or openly-licensed only (Project Gutenberg, Wikisource, Internet Archive PD scans, Standard Ebooks, sacred-texts). See PLAN.md for the two gates.",
  "objective": "Define the per-tale schema and its machine artifact (schema/tale.schema.json): id, title(s), culture/region/country, ATU type, Thompson motifs, language (BCP-47), artifactType (collected/translated/retold), a full source block with rights basis and verifier, translation/retelling provenance, a cultural-attribution block (with sacred-exclusion and TK context), content warnings, reading level/age range, output license, and a machine-readable provenance chain.",
  "acceptanceCriteria": [
    "Schema defines all per-tale fields including provenance, cultural attribution, ATU/motif, BCP-47 language, reading level/age, and content warnings.",
    "artifactType distinguishes collected, translated, and retold artifacts, each with its own provenance fields.",
    "'origin: uncertain' is a permitted honest value; no field permits a guessed value.",
    "Cultural-attribution block supports general vs. living-tradition classification and TK label/notice context.",
    "Every tale reserves a resolvable source-edition citation slot (edition/page-level) plus a rights-basis field.",
    "Published as a human-readable spec plus a machine artifact (schema/tale.schema.json) validated by an example tale."
  ],
  "resources": [
    "planning/projects/world-folktales-open/PLAN.md",
    "packages/schema/src/schemas.ts",
    "https://www.wikidata.org/",
    "https://localcontexts.org/",
    "https://en.wikipedia.org/wiki/Aarne%E2%80%93Thompson%E2%80%93Uther_Index"
  ],
  "output": "A tale schema specification document plus schema/tale.schema.json defining every per-tale field (provenance, cultural attribution, ATU/motif, language, reading level, content warnings, license), committed via PR.",
  "requestor": "jdev1977",
  "verifiedNeed": false,
  "outputLicense": "CC0-1.0"
}
```
