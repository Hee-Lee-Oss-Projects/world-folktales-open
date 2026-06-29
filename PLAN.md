# PLAN — world-folktales-open

> Status: Draft · Version: 0.1.0 · Last updated: 2026-06-28 · Owner: TBD (maintainer) · Lane: donated

An open, multilingual, fully-sourced commons of the world's folktales — collected, faithfully
translated, and (where appropriate) gently retold for young readers — built **only** from
public-domain and openly-licensed sources, where **every tale carries both a verifiable copyright
provenance and a respectful cultural attribution**. Copyright clearance alone is never enough: a
tale that is public domain in law can still be sacred or restricted in its living culture, and this
project treats *cultural permission* as a first-class gate beside *legal permission*.

**Positioning.** The world's folktales are humanity's shared inheritance, yet online they are
scattered across paywalled anthologies, link-rotted hobby sites, OCR garbage, and translations of
uncertain copyright — with origin cultures frequently uncredited, flattened, or mis-attributed.
`world-folktales-open` is the place where a teacher, parent, translator, or language community can
find a folktale that is **(a) legally free to reuse, (b) traceable to a named public-domain source,
(c) attributed to its culture of origin with care, and (d) available — or translatable — in their
language.** It is a content/data commons, not an app.

**Who it is for.** Educators and homeschoolers; children and families; literacy and
language-revitalization communities; libraries and cultural-heritage organizations; folklorists and
students; and downstream open projects (`literacy-from-zero`, `decodable-readers`,
`open-childrens-books`, `read-aloud-audio`, `public-domain-translations`) that can build on a clean,
attributed corpus.

**Constraints as identity.** Three refusals define the project: **no copyright-laundering** (no
modern copyrighted translation or anthology re-published as if PD); **no cultural appropriation of
restricted knowledge** (no sacred, secret, or community-restricted story reproduced just because the
*letter* of copyright law would permit it); and **no AI-invented "folklore"** (we collect, translate,
and retell what real sources attest — we never fabricate a tale and pass it off as traditional).

**Locked decisions (M0 ratifies the open ones):**
- **Stack:** TypeScript + ESM + pnpm tooling (per Elyos conventions); content as Markdown + YAML
  front-matter; canonical export as JSON + JSON-LD; static explorer; no accounts, no PII, no server.
- **Classification:** align every tale to the **Aarne–Thompson–Uther (ATU) tale-type index** and
  record **Thompson Motif-Index** motifs where known, so the corpus is interoperable with
  folkloristics scholarship from day one.
- **Identifiers:** host-independent persistent IDs (w3id.org / PURL) for every tale, decoupled from
  the (unsecured) steward.
- **Default output licence:** **CC BY 4.0** for new translations and retellings (attribution carries
  the cultural credit); **CC0 / "as-source"** for verbatim reproductions of pure-PD text;
  **CC BY-SA 4.0** only where CC BY-SA source material (e.g., Wikisource text) is incorporated.

Risk tier: **low overall**, with two parts that rise to **medium** — **translations/retellings**
(domain-accuracy review) and **living-tradition / Indigenous material** (cultural-sensitivity review).
There is no medical/legal/safety content, so no `high`-tier expert sign-off is required; the cultural
reviewer is this project's analogue of a domain expert.

## Executive summary

Folktales are public-domain at the level of the *ancient story*, but the artifacts people actually
reuse online — a specific 1990s translation, a copyrighted anthology's selection and arrangement, a
modern illustrated retelling — are very often **still under copyright**. The result is a minefield:
well-meaning educators copy material they have no right to reuse, origin cultures go uncredited, and
the genuinely free sources (Project Gutenberg, Wikisource, Internet Archive PD scans, sacred-texts
archives) are unstructured, inconsistently attributed, and hard to search by language, region, or
tale type.

This project builds an openly-licensed, structured corpus of folktales where **every tale carries a
machine-checkable provenance chain** — the exact public-domain or openly-licensed source edition, its
rights basis, the translation/retelling lineage, and a **cultural attribution** naming the originating
tradition. The corpus is classified by ATU tale type, available in multiple languages (PD source
translations plus new CC-BY translations and child-friendly retellings), and published as JSON/JSON-LD
plus a simple reader, so it is usable by non-technical educators and machine-consumable by other open
projects.

The two headline gates (see [Data, licensing & compliance](#data-licensing--compliance)) are
**(1) copyright/PD verification of the specific edition used** — *the original being old does not make
a modern translation free* — and **(2) cultural permission and attribution** — *being public domain in
law does not make a sacred or community-restricted story free to reproduce.* These two gates, applied
before any tale is published, are what separate this from the many sloppy folktale sites it aims to
replace.

A named **partner/steward who will adopt, host long-term, and cite the corpus is TO BE SECURED.** The
*gap* is real and demonstrable, but per the Elyos quality bar ("delivered, not merged") a committed
last-mile beneficiary has not yet signed on; securing one is a first-class M0–M3 objective and a
precondition for declaring the project *shipped*. `verifiedNeed` is therefore `false` on all tasks
until a partner is secured.

## Problem & beneficiaries

**The problem.**
- **Copyright fog.** The underlying tale is ancient and free, but the *translation, selection,
  arrangement, illustration, and retelling* that make a usable artifact are frequently under
  copyright. "It's a folktale, so it's public domain" is a false and legally dangerous shortcut.
- **Cultural erasure & harm.** Origin cultures are routinely uncredited or mis-attributed ("a
  Cinderella story" with no acknowledgment of the specific tradition). Worse, some material — sacred,
  ceremonial, secret/sacred, or seasonally restricted stories, especially Indigenous — is reproduced
  online merely because copyright lapsed, ignoring that the originating community never consented and
  that **copyright public-domain status carries no cultural permission whatsoever.**
- **Fragmentation & rot.** Free sources exist but are scattered, link-rotted, OCR-corrupted,
  inconsistently structured, and not searchable by language, region, reading level, or tale type.
- **Language scarcity.** Most quality folktale collections are in a handful of colonial languages;
  low-resource and revitalizing language communities have few open, reusable, child-appropriate texts.

**Beneficiaries.**
- **Educators, homeschoolers, and literacy programs** needing free, attributed, reading-level-tagged
  stories they can legally copy, translate, and remix.
- **Children and families** — culturally diverse, age-appropriate stories in their own language.
- **Language-revitalization & low-resource-language communities** who can translate a clean,
  rights-clear source into their language and own the result (CC BY).
- **Libraries, museums, and cultural-heritage organizations** wanting a citable, provenance-rich
  reference corpus.
- **Folklorists, educators, and students** who get an ATU-classified, source-linked dataset.
- **Originating cultures** — through accurate, respectful, credited representation (a benefit only if
  the cultural gate is honored; a harm if it is not).
- **Downstream open projects** (`literacy-from-zero`, `decodable-readers`, `read-aloud-audio`,
  `public-domain-translations`, `open-childrens-books`) that reuse the corpus.

**Verified need.** The *gap* (no open, structured, dual-gated, multilingual folktale commons) is
real. However, a **named partner organization or steward who will adopt, host, and cite the output is
TO BE SECURED.** No committed last-mile beneficiary has signed on; securing one is an M0–M3 objective
and a precondition for "shipped." `verifiedNeed` stays `false` on tasks until then.

**Partner org.** TO BE SECURED. Candidate stewards: a public library / digital-collections team, the
American Folklore Society or a national folklore society, a university folklore/digital-humanities
program, a literacy NGO, a language-revitalization community organization, or an existing PD-text
steward (Project Gutenberg / Standing Ebooks / Wikisource community). For living-tradition material,
the relevant **originating-community representatives** are the partners whose consent governs reuse.

## Goals and non-goals

**Goals**
- Publish an openly-licensed, structured corpus of world folktales with **provenance on every tale**
  (source edition + rights basis) and a **cultural attribution** on every tale.
- Verify the **specific edition's** copyright status — never assume PD from the tale's age.
- Apply a **cultural-permission gate**: exclude sacred/restricted material; for living-tradition and
  Indigenous stories, require evidence of community-open status or community consent, and attach
  Traditional Knowledge (TK) context where applicable.
- Classify tales by **ATU tale type** and Thompson motifs; record region, culture, and language
  (BCP-47).
- Provide tales in multiple languages: PD source translations, **new CC-BY translations**, and
  optional **child-friendly retellings** — each with its own provenance and review.
- Tag **reading level / age range** and **content warnings** so the corpus is usable by educators.
- Publish JSON + JSON-LD exports and a simple, accountless, PII-free reader/explorer.
- Secure at least one steward that adopts and cites the corpus.

**Non-goals**
- **Not** a re-publisher of copyrighted translations, anthologies, illustrations, or retellings —
  even of an ancient tale. The *artifact's* rights govern, not the tale's age.
- **Not** a vehicle for sacred, secret, ceremonial, or community-restricted stories. Copyright lapse
  is **not** cultural permission; when in doubt, exclude and flag.
- **Not** an inventor of folklore — no AI-fabricated "traditional" tales, no invented provenance, no
  guessed attribution. Gaps stay gaps.
- **Not** a scraper of paywalled or terms-restricted anthology sites; not a mirror of any source
  whose terms forbid reuse.
- **Not** a children's-illustration project (illustrations are a separate, later, rights-cleared
  effort — see `open-childrens-books`); text-first here.
- **Not** an academic authority that adjudicates a tale's "true" origin; it records sourced claims and
  surfaces scholarly disagreement.
- **Not** a platform with user accounts, comments, uploads-of-record, or any PII collection.
- **Not** audio/narration (that is `read-aloud-audio`); this corpus is the clean text it builds on.

## Success metrics (outcomes)

Outcome-based and beneficiary-centric. Baselines are zero at project start unless noted.

| Metric | Baseline | Target (first 12 months) |
| --- | --- | --- |
| Tales published with a verified PD/open **source-edition** citation | 0 | ≥ 300 |
| Share of published tales carrying a **resolvable source-edition citation** | n/a | **100%** (hard gate; un-sourced tales are not published) |
| Share of published tales carrying a **cultural attribution** (origin tradition named, or "origin uncertain" recorded honestly) | n/a | **100%** (hard gate) |
| Living-tradition / Indigenous tales passing the **cultural-permission review** before publish | n/a | **100%** (hard gate; unreviewed = unpublished) |
| Distinct cultures / regions represented | 0 | ≥ 25 regions |
| Distinct languages with ≥1 complete tale | 0 | ≥ 10 languages |
| New CC-BY translations or retellings published with language + cultural review | 0 | ≥ 60 |
| Translation/retelling accuracy: sampled items passing **back-check** against source meaning | n/a | ≥ 95% of a stratified audit sample (see frame below) |
| Copyright-audit pass rate (sampled tales whose cited edition is confirmed PD/open) | n/a | **100%** (any failure is a recall-and-fix event, not a tolerated error rate) |
| Tales with reading-level / age-range metadata | 0 | ≥ 80% of published tales |
| Steward/partner adoptions citing or hosting the corpus | 0 | ≥ 1 committed steward; ≥ 1 documented citation/use |
| Reuse (downloads / API pulls / downstream-project ingests) | 0 | tracked from M2; growth reported quarterly |

**Audit sampling frame (pins the accuracy & copyright metrics).** Each release is audited with a
**minimum sample of 50 tales** (or the whole release if smaller), **stratified by** (a) rights basis
(verbatim-PD vs. new-translation vs. retelling) and (b) cultural category (general/literary vs.
living-tradition/Indigenous), so no category escapes review. The **auditor is independent of the
contributor** of the sampled items (no self-grading). Translation accuracy uses a **back-check**:
re-reading the source and confirming the new text preserves meaning, register, and key cultural
detail without distortion.

We explicitly **do not** count tales-merged, PRs, or commits as success. A large corpus with weak
provenance or careless cultural attribution is a **failure** under this plan.

## Scope

**In scope**
- A tale data model (schema) with provenance, cultural attribution, ATU/motif classification,
  language, reading level, and content warnings.
- A source allow-list with **per-edition** rights determination (`approved | rejected | pending`).
- Collection of verbatim public-domain tales from approved sources.
- **New translations** (into low-resource and other languages) and **child-friendly retellings**,
  each provenance-linked and reviewed.
- ATU/motif alignment and cross-linking of tale variants across cultures.
- Cultural attribution and the cultural-permission review workflow (incl. TK context where relevant).
- JSON + JSON-LD exports, a static reader/explorer, reading-level and content-warning metadata.
- Outreach for a steward and for originating-community partners where living-tradition material is in
  scope.

**Out of scope (explicit)**
- **Any re-publication of copyrighted translations, anthologies, selections/arrangements,
  illustrations, or retellings** — even of an ancient, PD tale. Hard refusal; not a deprioritized item.
- **Any sacred, secret, ceremonial, or community-restricted story**, and any living-tradition /
  Indigenous material lacking evidence of community-open status or consent. Copyright PD ≠ cultural
  permission. When in doubt, exclude and flag.
- **AI-fabricated tales**, invented attributions, or guessed provenance. Gaps stay gaps.
- Scraping paywalled or terms-restricted sites; mirroring any source whose terms forbid reuse.
- Illustration, audio/narration, accounts, comments, uploads-as-record, or any PII collection.
- Adjudicating contested origins; "certifying" a single authoritative version.

## Solution approach & architecture

A **content/data pipeline** project (with supporting TypeScript tooling), not a hosted service.

**Pipeline stages**
1. **Source intake & dual-gate** — each candidate source/edition is logged in
   `sources/allowlist.yml` with: title, author/collector, translator, edition year, publisher,
   custodian/host, URL, format, **rights basis** (PD-by-age, PD-as-US-gov, CC0, CC BY, CC BY-SA,
   etc.), the **specific-copy rights analysis**, and `status: approved | rejected | pending`. A
   parallel **cultural classification** records: originating tradition (best-sourced), whether the
   material is **general/literary** or **living-tradition/Indigenous**, and a sensitivity flag.
   Nothing is processed until the rights gate is `approved` **and** the cultural gate is cleared.
2. **Tale schema layer** — a documented schema (`schema/tale.schema.json`) for each tale (fields in
   the data model below), with ATU and BCP-47 vocabularies.
3. **Collection / extraction** — verbatim PD tales are transcribed from approved sources. **OCR is
   used only on machine-print PD scans**, with a transcription-accuracy threshold; OCR output is
   human-corrected against the source image, and both the text and a page/edition-level citation are
   retained. Extraction is **assistive** — ambiguous text is flagged, never guessed.
4. **Translation / retelling** — new translations and child-friendly retellings are produced as
   *derived* artifacts that point to their PD source tale, carry their own contributor + reviewer
   provenance, and (for retellings) a **change note** explaining what was simplified and why, so
   distortion is auditable.
5. **Cultural review** — every living-tradition/Indigenous tale, and every retelling, passes a
   cultural-sensitivity review (TK context attached where relevant; sacred/restricted items rejected).
6. **Validation** — JSON-Schema validation + a **provenance-completeness linter** and an
   **attribution-completeness linter** in CI (no tale ships without a resolvable source citation and a
   cultural attribution).
7. **Publish** — versioned JSON + JSON-LD dumps, a static reader/explorer, and per-tale persistent
   IDs under the project's w3id/PURL namespace.

**Tech stack**
- Tooling, validators, build: **TypeScript, ESM, pnpm** (per Elyos conventions).
- Content: **Markdown body + YAML front-matter** per tale; canonical **JSON + JSON-LD** export.
- Validation: **JSON Schema (Ajv)** + custom provenance/attribution linters wired into CI.
- Classification vocab: **ATU tale-type index** + **Thompson Motif-Index**; **BCP-47** languages;
  schema.org `CreativeWork` alignment in JSON-LD.
- Reader/explorer: a **static site** over the JSON (no accounts, no server-side, no PII); links to raw
  exports and to each tale's source.

**Data model (per tale)**
- `id` — persistent w3id/PURL slug. `title` (per language); `aka` (alternate titles).
- `culture` / `region` / `country` — originating tradition (best-sourced; `origin: uncertain` allowed
  and recorded honestly, never guessed).
- `atuType` (e.g., `ATU 510A`) and `motifs[]` (Thompson) where known.
- `language` (BCP-47); `artifactType: collected | translated | retold`.
- `source` — `{ title, author/collector, translator, editionYear, publisher, host, url, rightsBasis,
  rightsAnalysis, rightsVerifiedBy, accessPath }`.
- `translationProvenance` / `retellingNote` — lineage for derived artifacts (translator/reteller,
  base tale id, reviewer, change summary).
- `culturalAttribution` — `{ originTradition, category: general|living-tradition, tkLabels?,
  sensitivityReview: {reviewer, outcome}, communityConsentEvidence? }`.
- `contentWarnings[]`, `readingLevel` / `ageRange`.
- `license` — output licence (CC BY 4.0 / CC0 / CC BY-SA 4.0 / "as-source").
- `provenanceChain` — the full source→derivation lineage, machine-readable.

**Key decisions (M0 ratifies)**
- **Dual-gate is mandatory and ordered:** the cultural gate can reject a tale that *passes* the
  copyright gate; copyright clearance is necessary but never sufficient.
- **Persistent IDs** under w3id/PURL, decoupled from any host/steward (so IDs survive a steward
  change or never being secured).
- **Verbatim vs. derived licensing:** verbatim PD → CC0/"as-source"; new translation/retelling →
  CC BY 4.0; any CC BY-SA source incorporated → CC BY-SA 4.0, labeled at the tale level.

## Data, licensing & compliance

**This is the headline section. Read it before any data work. There are TWO gates, not one.**

### Gate 1 — Copyright / public-domain verification (of the specific edition)

The ancient tale is free; **the artifact you actually reuse may not be.** Copyright can subsist in a
**translation**, an **anthology's selection/arrangement**, **editorial apparatus**, **illustrations**,
and **modern retellings** — independently of the underlying tale being PD. Therefore:

- **Verify the specific copy/edition/translation, not the tale's age.** Each `sources/allowlist.yml`
  entry records the rights basis for *that edition* (e.g., "Margaret Hunt's 1884 English translation of
  Grimm — PD by age" is fine; a 1987 Penguin translation of the same Grimm tale is **not**).
- **PD determination is jurisdiction-aware.** Record the basis: US PD (pre-1929 published, or US-gov
  work), `life+70` expiry, CC0, CC BY, CC BY-SA, etc. Where jurisdictions differ, note it; default to
  the most conservative reuse posture.
- **No copyright-laundering.** A contributor must not copy a copyrighted translation/retelling and
  back-fill a plausible PD citation. Controls: **edition/page-level citations required** (never
  "from a collection"); **contributor attestation of independent, rights-cleared sourcing**; and
  **reviewer spot-checks** for tell-tale modern phrasing or anthology-distinctive editorial artifacts
  that would not appear in the cited PD edition. A hit triggers rejection and a flag.

**Candidate approved sources (verify per edition before use):**
- **Project Gutenberg** — PD e-texts (e.g., Grimm via Margaret Hunt; Andersen via PD translators;
  Joseph Jacobs's *English/Celtic/Indian Fairy Tales*; Andrew Lang's colored *Fairy Books*; Lafcadio
  Hearn and Yei Theodora Ozaki for Japanese tales). Verify each title's PD basis and translator.
- **Wikisource** — PD texts (and **CC BY-SA** community text — triggers share-alike; segregate/label).
- **Internet Archive** — PD scans (verify the *scan's* and the *edition's* rights, not just the work's).
- **Standard Ebooks** — PD source texts (their typesetting is CC0).
- **sacred-texts.com and similar archives** — predominantly PD source texts; verify each.
- **Wikidata** (CC0) — for ATU/motif/region reconciliation and cross-variant linking.

**Caveats we will not gloss over:** a PD tale can be wrapped in a copyrighted scan, a copyrighted
translation, or a copyrighted compilation; "public domain" must be verified for the **specific copy,
edition, and translation** used. Each allow-list entry records this analysis; pending = unusable.

### Gate 2 — Cultural permission & attribution (copyright PD ≠ cultural-open)

A story can be public domain in copyright law and still be **sacred, secret, ceremonial, seasonally
restricted, or otherwise not meant for outside reproduction** — particularly Indigenous and
living-tradition material. Copyright lapse confers **no** cultural permission. Therefore:

- **Classify every tale** as **general/literary** (e.g., long-published European literary fairy tales,
  Aesop) or **living-tradition / Indigenous**. The two are reviewed differently.
- **Living-tradition / Indigenous material requires evidence of community-open status or consent.**
  Acceptable bases: the originating community has itself openly published/shared it for reuse; a
  recognized cultural-heritage steward has released it openly; or documented community consent exists.
  **Absent such evidence, the tale is excluded and flagged** — we do not reproduce it merely because a
  copyright clock expired.
- **No sacred / secret / restricted stories**, full stop, regardless of copyright status. When a
  tale's status is uncertain, the default is **exclude and flag for the cultural reviewer**, not
  publish.
- **Attribution with care.** Name the originating tradition accurately; record `origin: uncertain`
  honestly rather than guessing; avoid colonial framings; attach **Traditional Knowledge (TK) Labels /
  Notices (Local Contexts)** and follow the **CARE Principles for Indigenous Data Governance** where
  applicable.
- **Retellings carry a distortion risk** — simplifying for children can strip or warp cultural meaning.
  Every retelling records a **change note** and passes cultural review.

### Provenance model
- **Every tale** links to its source edition at **edition/page-level** granularity, with the rights
  basis, the verifier, and (for derived works) the full translation/retelling lineage.
- Un-sourced or un-attributed tales are **never published** — enforced as CI gates.
- Conflicting origin/variant claims are retained side by side with their sources; no forced "winner."

### Privacy / PII stance
- Subjects are **fictional/legendary characters**; minimal PII surface.
- Where a tale was **collected from a named informant or community**, credit per the source but
  **collect no private data about living people**; no contact details, no sensitive personal data.
- No visitor/contributor PII beyond the standard open-source attribution a contributor opts to give.

### Attribution & output licence
- **Code:** MIT. **Content:** **CC BY 4.0** for new translations/retellings (attribution carries the
  cultural credit); **CC0 / "as-source"** for verbatim pure-PD reproductions; **CC BY-SA 4.0** where
  CC BY-SA source text (e.g., Wikisource) is incorporated, labeled at the tale level.
- Required attributions (source edition, translator, originating culture, CC BY-SA upstreams, TK
  notices) are recorded and surfaced on every tale.

## Quality, review & risk gates

**Risk tier: low overall; medium for translations/retellings and for living-tradition material.** No
medical/legal/safety content ⇒ no `high`-tier credentialed sign-off. Three review dimensions, applied
before a tale is "done":

1. **Copyright/PD review (primary gate, all tales).** A reviewer confirms the `allowlist.yml` entry:
   the *specific edition/translation* is PD or openly licensed and not a laundered modern artifact. No
   collection task starts against a `pending`/`rejected` source. Any task proposing to reuse
   copyrighted material is **refused and flagged** per Elyos guardrails.
2. **Cultural-sensitivity review (living-tradition material + all retellings).** A reviewer with
   relevant cultural competence confirms the tale is not sacred/restricted, that attribution is
   accurate and respectful, and that any retelling preserves meaning. Sacred/restricted ⇒ rejected.
3. **Translation/retelling accuracy review (medium-risk).** A language-fluent reviewer back-checks new
   translations/retellings against the source for meaning, register, and cultural detail.

**Definition of Shipped (project level).** A published, openly-licensed, ATU-classified folktale
corpus with: **100%** of tales carrying a resolvable source-edition citation; **100%** carrying a
cultural attribution; **100%** of living-tradition/retold items cleared by cultural review; ≥25 regions
and ≥10 languages; passing JSON-Schema + provenance + attribution CI; with at least one **steward that
has adopted or cited** it. Per Elyos, *delivered ≠ merged* — it must be in a beneficiary's hands.

**Per-deed Definition of Done.** Acceptance criteria met + CI green (schema/provenance/attribution) +
copyright review passed + (where applicable) cultural + accuracy review passed + published under the
declared licence.

## Roadmap & milestones

**M0 — Foundation & dual-gate spine (cold-start).**
Goal: build the rails so no tale can bypass the copyright **or** cultural gate.
Exit criteria: (a) tale schema v0 published (provenance, cultural attribution, ATU/motif, language,
reading level, content warnings); (b) `sources/allowlist.yml` schema + dual-gate policy defined, with
≥3 sources analyzed and ≥1 `approved`; (c) cultural-attribution & sensitivity policy published
(general vs. living-tradition; sacred/restricted exclusion; TK/CARE guidance; copyright-PD ≠
cultural-open stated explicitly); (d) CI provenance-completeness + attribution-completeness + schema
linters scaffolded; (e) persistent-ID (w3id/PURL) namespace committed; (f) **a qualified copyright
reviewer named** (hard exit; documented fallback if the seat is empty — M0 cannot exit, escalate);
(g) partner/steward outreach started and status logged.

**M1 — First sourced slice (proof of pipeline).**
Goal: end-to-end ~25 verbatim PD tales from clearly-PD English-language sources, fully gated.
Hard entry precondition: each source edition is recorded in the allow-list as PD-verified before
transcription. Exit criteria: (a) ≥25 verbatim PD tales published, each with edition/page-level
citation, ATU type, and a cultural attribution; (b) **100%** provenance + attribution pass CI; (c) any
living-tradition item among them cleared by cultural review (or excluded+flagged); (d) JSON + JSON-LD
export produced under the persistent-ID namespace; (e) ≥1 candidate steward in conversation; (f) a
**cultural reviewer named** before any living-tradition item is published. Depends on M0.

**M2 — Multilingual, retellings & reader (usable surface).**
Goal: make the corpus multilingual, child-usable, and browsable.
Exit criteria: (a) ≥30 new CC-BY translations and/or child-friendly retellings, each with
translation/cultural/accuracy review and a retelling change note; (b) reading-level/age + content
warnings on ≥80% of tales; (c) static reader/explorer + documented exports live (no accounts/PII);
(d) ≥10 languages with ≥1 complete tale; (e) reuse metrics tracked. Depends on M1.

**M3 — Scale & steward adoption (shipped).**
Goal: breadth across cultures/languages and real-world adoption.
Exit criteria: (a) ≥300 tales across ≥25 regions and ≥10 languages; (b) ≥1 steward has **adopted or
cited** the corpus (Definition of Shipped met); (c) cultural-review and copyright-audit pass rates met
(100% on the hard gates; ≥95% accuracy on the sampled frame); (d) sustainability/maintenance plan in
effect. Depends on M2.

## Work breakdown

The itemized, schema-mapped backlog lives in [`TASKS.md`](./TASKS.md), organized by the milestones
above (M0–M3) plus a sized backlog. Each task maps to an Elyos Task JSON with type, size, risk tier,
deliverable, dependencies, and reviewer. M0 deliberately front-loads **both** the copyright and the
cultural gates before any bulk collection begins.

## Governance, roles & stakeholders

- **Maintainer / Owner:** TBD — accountable for scope, both gates, and releases.
- **Copyright / PD reviewer:** TBD — approves every `allowlist.yml` edition entry; veto over any
  source. **Naming a qualified person is a hard M0 exit criterion.** *Fallback if empty:* no source
  advances past `pending`, no collection begins, M0 cannot exit; maintainer escalates to Elyos
  governance (and may engage pro-bono counsel) before any data work.
- **Cultural-sensitivity reviewer(s) (rotation):** people with relevant cultural competence — ideally
  including representatives of originating communities for living-tradition material. **Required before
  any living-tradition tale or retelling is published.** TO BE SECURED.
- **Language/translation reviewers (rotation):** fluent reviewers for each target language. TO BE
  SECURED per language.
- **Steward (last-mile owner):** the library / folklore society / heritage org / language community
  that adopts, hosts long-term, and cites the corpus. **TO BE SECURED** — required for "shipped."
- **Originating-community partners:** for living-tradition material, the communities whose consent
  governs reuse. TO BE SECURED per culture, as needed.
- **Partner / requestor:** educators, families, language communities, libraries (diffuse beneficiary
  class); a named representative org is TO BE SECURED.
- **Elyos governance/board:** arbiter for edge cases (a borderline source; a contested cultural
  status) under the published conflict-of-interest/veto checklist.

## Dependencies & integrations

- **Project Gutenberg, Wikisource, Internet Archive, Standard Ebooks, sacred-texts** (PD/open
  sources; verify per edition).
- **ATU tale-type index** and **Thompson Motif-Index** (classification vocab; cite editions).
- **Wikidata** (CC0) for reconciliation and cross-variant linking.
- **Local Contexts (TK Labels/Notices)** and **CARE Principles** (cultural-governance frameworks).
- **JSON Schema / Ajv**, a Markdown+YAML toolchain, and a static-site generator (TS/ESM ecosystem).
- **Elyos pieces:** Task schema (`packages/schema`), CLI workspace/PR flow (`packages/cli`,
  `packages/core`), governance proposal/registry process. Donated lane — humans run their own agents.
- **Sibling Elyos projects** as consumers: `literacy-from-zero`, `decodable-readers`,
  `read-aloud-audio`, `public-domain-translations`, `open-childrens-books`.

## Risks & mitigations

| Risk | Likelihood | Impact | Mitigation | Owner |
| --- | --- | --- | --- | --- |
| Contributor reuses a **copyrighted translation/retelling/anthology** (incl. laundered via a fake PD citation) | High | Critical (legal; project-ending) | Per-edition rights gate; allow-list blocks un-approved sources; copyright-reviewer veto; CI rejects unapproved sources; **edition/page-level citations + contributor attestation + reviewer spot-checks for modern phrasing**; refuse + flag | Copyright reviewer |
| **Sacred / restricted / non-consented** living-tradition material reproduced because copyright lapsed | Medium | Critical (cultural harm, irreversible) | **Cultural gate independent of the copyright gate**; living-tradition items require community-open evidence/consent; sacred/restricted excluded; default to exclude-and-flag when uncertain; TK/CARE guidance | Cultural reviewer |
| "PD original" wrapped in a **copyrighted scan, translation, or compilation** | High | High | Per-copy/edition rights analysis recorded; verify the specific digitization/translation, not the tale's age | Copyright reviewer |
| **Mis-attribution / cultural erasure** (wrong or no origin culture) | Medium | High | Mandatory cultural-attribution field; `origin: uncertain` recorded honestly; cultural review; avoid colonial framings | Cultural reviewer |
| **Retelling distorts** cultural meaning when simplified for children | Medium | High | Required change note per retelling; cultural + accuracy review; faithfulness back-check | Cultural + language reviewers |
| **Translation inaccuracy** (meaning/register lost) | Medium | Medium | Language-fluent reviewer back-check; stratified accuracy audit ≥95%; assistive (not autonomous) translation | Language reviewer |
| **No steward/partner secured** → "delivered ≠ merged" not met | High | High | Treat outreach as an M0–M3 deliverable; log status honestly; pursue multiple candidate stewards | Maintainer |
| **AI-fabricated "folktale"** or invented provenance/attribution | Medium | High | Sources-only rule; provenance + attribution CI gates; gaps stay gaps; reviewer spot-checks | Maintainer |
| **OCR / transcription errors** corrupt the text | Medium | Medium | OCR only on PD machine-print; human correction against source image; accuracy threshold gate | Maintainer |
| **CC BY-SA (Wikisource) text contaminates** a CC0/CC-BY dataset | Medium | Medium | Prefer CC0 sources; label CC BY-SA-derived tales; tale-level licence honesty | Maintainer |
| **Reviewer capacity exhausted** (copyright + cultural + language review become a bottleneck) | Medium | High | Sampling-based audits (not 100% re-check) for accuracy; reviewer rotation with response-time SLA; throughput ceiling that throttles intake when backlog exceeds it | Maintainer |
| **ID/host instability** breaks tale links | Medium | Medium | Host-independent w3id/PURL IDs committed in M0; redirect strategy | Maintainer |
| **Scope creep** into illustration/audio/platform | Medium | Medium | Explicit non-goals; governance review of scope changes | Maintainer |

## Security & privacy

- **Threat surface:** small (content/data project; no accounts, no server-side, no visitor PII). Main
  risks are *compliance* (copyright + cultural) and *integrity* (false/unsourced/mis-attributed tales),
  addressed by the gates above.
- **Secrets handling:** PD/open sources need no API keys; any reconciliation credentials stay out of
  logs, receipts, and commits per Elyos rules. The donated lane never runs headless or authenticates
  an agent.
- **PII:** fictional characters; no private data about living informants/communities beyond the credit
  the source already publishes; no visitor data; contributor attribution is opt-in and minimal.
- **Abuse/misuse prevention:** every tale is source-linked and attribution-checked, so claims are
  auditable; the project refuses and flags attempts to launder copyrighted text or to reproduce
  sacred/restricted material. No surveillance or personal-data use is supported.

## Sustainability & maintenance

- **After delivery,** the maintainer plus the secured steward own ongoing curation; the steward
  provides long-term hosting, while the **canonical persistent IDs (w3id/PURL) are owned by the
  project, not the host**, so tale links survive a steward change and the corpus is never orphaned.
- **Reviewer sustainability:** accuracy review runs on **sampling**, not exhaustive re-checking; the
  two hard gates (copyright, cultural) are 100% but lightweight per tale; reviewers work a **rotation
  with a response-time SLA**; a **throughput ceiling** throttles new intake when the review backlog
  grows, so quality gates never silently degrade.
- **Outcome tracking:** quarterly report on tale count, provenance completeness (must stay 100%),
  attribution completeness (100%), cultural-review coverage of living-tradition items (100%),
  languages/regions, accuracy-audit pass rate, steward adoptions, and reuse/downloads.
- **Contributions** continue via the donated lane under the same dual-gate + accuracy review.
- **Versioned releases** (with changelogs) keep downstream consumers (`literacy-from-zero`, etc.)
  stable.
- If no steward is secured, the project stays in a maintained-but-not-shipped state and the gap is
  reported honestly rather than declared done.

## Open questions

- Who is the committed steward / adopting partner? (TO BE SECURED — blocks "shipped.")
- Who staffs the **cultural-sensitivity reviewer rotation**, and how are originating-community
  representatives engaged and (where appropriate) compensated for living-tradition material?
- Which initial **target languages** for new translations (driven by the language communities we can
  partner with)?
- Default content licence per artifact type confirmed (CC BY 4.0 derived / CC0 verbatim / CC BY-SA
  segregated) — ratify in M0.
- Which **ATU/Motif-Index editions** are citable without rights issues, and how deep to classify?
- How to represent **multiple variants** of the same tale type across cultures without implying one is
  the "real" version?
- Scope and process for accepting **community-contributed** living-tradition tales (consent workflow).

## References

- Project proposal: `governance/proposals/world-folktales-open.md` (TO BE CREATED)
- Elyos work rules: `CLAUDE.md`
- Good Deed Definition & risk tiers: `docs/good-deed-definition.md`
- Task JSON schema: `packages/schema/src/schemas.ts`
- Portfolio roadmap: `planning/ROADMAP.md`
- Sources: Project Gutenberg; Wikisource; Internet Archive; Standard Ebooks; sacred-texts.com
- Classification: Aarne–Thompson–Uther (ATU) tale-type index; Thompson Motif-Index of Folk-Literature
- Cultural governance: Local Contexts — Traditional Knowledge (TK) Labels/Notices; CARE Principles for
  Indigenous Data Governance
- Reconciliation vocab: Wikidata (CC0); schema.org `CreativeWork`; BCP-47 language tags

---

## Appendix A — Improvements applied

The following 25 specific improvements were identified against the first draft and **applied** in the
text above (not merely listed).

1. **Split the single "license/provenance" gate into two independent gates** (copyright *and*
   cultural), since the project's distinctive risk is that PD-in-law ≠ culturally-open. Reflected in
   the executive summary, §Data/licensing, §Quality, and the risk table.
2. **Made the cultural gate able to override a passing copyright gate** and ordered them, so a tale can
   be legally free yet still rejected. Stated explicitly under "Key decisions" and Gate 2.
3. **Added a sacred/secret/restricted-material exclusion** with an explicit "when in doubt, exclude and
   flag" default, rather than a permissive default.
4. **Cited concrete cultural-governance frameworks** (Local Contexts TK Labels/Notices; CARE
   Principles) instead of a vague "be respectful," giving reviewers something enforceable.
5. **Per-edition copyright verification** replaced "verify license," with the worked Grimm example
   (Margaret Hunt 1884 PD vs. 1987 Penguin not), to kill the "it's old so it's free" fallacy.
6. **Anti-laundering controls** (edition/page-level citations, contributor attestation, reviewer
   spot-checks for modern phrasing) ported from the patriots-KG pattern and adapted to translations.
7. **ATU tale-type + Thompson Motif-Index classification locked as a stack decision**, making the
   corpus interoperable with folkloristics and enabling cross-cultural variant linking.
8. **Distinguished three artifact types** (collected / translated / retold) with different provenance
   and review paths, instead of treating all tales identically.
9. **Required a retelling "change note"** so child-friendly simplification is auditable for distortion
   — closing a real cultural-harm vector.
10. **Pinned the accuracy/copyright audit sampling frame** (min 50, stratified by rights basis and
    cultural category, independent auditor, back-check method) so the ≥95% metric is meaningful.
11. **Separated hard 100% gates** (provenance, attribution, cultural review of living-tradition items,
    copyright pass) **from the sampled ≥95% accuracy metric**, so quality bars aren't conflated.
12. **Made `origin: uncertain` a first-class honest value**, forbidding guessed attributions — gaps
    stay gaps, consistent with the "no fabrication" rule.
13. **Host-independent persistent IDs (w3id/PURL) committed in M0**, decoupled from the unsecured
    steward, so links survive steward churn.
14. **`verifiedNeed=false` made explicit and consistent** across PLAN and every task until a partner is
    secured, per the honesty convention.
15. **Named the copyright reviewer as a hard M0 exit criterion** with a documented escalation fallback
    if the seat is empty (mirrors the licensing-gate rigor of the exemplar).
16. **Named the cultural reviewer as a precondition** before any living-tradition tale or retelling is
    published (M1 gate), not an afterthought.
17. **Reviewer-sustainability mechanisms** (sampling, rotation + SLA, throughput ceiling) added so the
    three review dimensions don't collapse under load.
18. **PII stance sharpened for collected-from-informant tales** — credit per source, but no private
    data about living people/communities.
19. **CC BY-SA contamination handled** (prefer CC0, segregate and label Wikisource-derived tales at
    the tale level) rather than a blanket licence claim.
20. **OCR policy bounded** (OCR only on PD machine-print, human-corrected against the source image,
    accuracy threshold) to prevent corrupt-text ingestion.
21. **Explicit non-goals carved out** illustration, audio, and platform features, with pointers to the
    sibling Elyos projects that own them — preventing scope creep.
22. **Downstream-consumer integration named** (`literacy-from-zero`, `decodable-readers`, etc.) so the
    corpus is positioned as reusable infrastructure, strengthening the "public benefit" case.
23. **Reading-level / age-range + content-warnings metadata** added as a first-class field and metric,
    because the headline beneficiaries are educators and families.
24. **Originating-community partners** added to governance as the consent-holders for living-tradition
    material (and an open question on engaging/compensating them).
25. **Risk table given explicit owners per row** and re-ranked so the two top risks (copyright
    laundering; sacred-material reproduction) are both Critical with distinct owners.

## Review sign-off

A completeness/correctness pass was performed against the PLAN_SPEC requirements and Elyos guardrails;
findings were fixed in-document.

- **Metrics measurable?** Yes — all success metrics have a baseline and a 12-month target; the
  audit-based ones (accuracy, copyright) name a sampling frame (min 50, stratified, independent
  auditor). Vanity metrics (PRs/commits) explicitly disclaimed.
- **Gates enforceable?** Yes — provenance, attribution, and source-approval are CI-enforced linters;
  the copyright and cultural gates are human reviews with named seats, vetoes, and documented empty-seat
  fallbacks; the cultural gate is independent of and can override the copyright gate.
- **Risks have owners + mitigations?** Yes — every row in the risk table has both; the two Critical
  rows (copyright laundering; sacred/restricted reproduction) carry distinct owners and concrete
  controls.
- **License / PII / expert guardrails?** Yes — open/PD/CC-only with per-edition verification; PII
  surface minimal and bounded; no medical/legal/safety content, so no `high`-tier sign-off needed —
  the cultural reviewer is the domain-expert analogue and is mandatory for living-tradition/retold work.
- **Sequencing sound?** Yes — M0 builds both gates before any bulk collection; M1 proves the pipeline
  on clearly-PD English tales; M2 adds multilingual/retellings + reader; M3 scales to the shipped bar.
  Dependencies are explicit in TASKS.md.
- **Schema-valid tasks?** Verified — the example Task JSON in TASKS.md validates against
  `packages/schema/src/schemas.ts` (all required fields present, enum values legal, `verifiedNeed:false`,
  real `outputLicense`).
- **Honest about gaps?** Yes — partner/steward, cultural reviewers, language reviewers, and the
  proposal file are all marked TO BE SECURED / TO BE CREATED; `verifiedNeed` is `false` throughout.

Outstanding items requiring a human decision are consolidated in [Open questions](#open-questions);
the project cannot be declared *shipped* until a steward is secured and the cultural-reviewer rotation
is staffed.
