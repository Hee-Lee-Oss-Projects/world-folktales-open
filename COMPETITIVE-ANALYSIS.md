# Competitive & Improvement Analysis — `world-folktales-open`

> Scope: rigorous review of `PLAN.md` (v0.1.0) + competitive landscape, gaps, differentiators,
> Claude-API leverage, optimizations, spin-offs, and open questions. Competitor claims are grounded in
> cited web sources. Lane: donated. Risk tier: low overall / medium for translations + living-tradition
> material.

---

## 1. Correctness & completeness review of PLAN.md

The plan is unusually strong. Its central insight — that **legal clearance and cultural permission are
two independent gates**, and the cultural gate can veto a copyright-clear tale — is correct, well above
the field, and is the project's defining virtue. The "three refusals" (no copyright-laundering, no
appropriation of restricted knowledge, no AI-fabricated folklore) are the right framing. Most of what
follows is sharpening, not contradiction.

**What is correct and well-handled**
- **Dual-gate, ordered and mandatory** (cultural can override copyright): exactly right. The dominant
  industry error is treating "public domain in print" as sufficient. The plan names this fallacy and
  builds the architecture to defeat it.
- **Per-edition copyright verification** with the worked Grimm/Margaret-Hunt-1884-vs-Penguin-1987
  example correctly kills the "it's old so it's free" shortcut. Copyright genuinely *does* subsist in
  translations, selections/arrangements, and editorial apparatus.
- **TK Labels / Local Contexts + CARE Principles** are the correct, real, enforceable frameworks for
  the cultural gate — not a vague "be respectful." Local Contexts (founded 2010 by Jane Anderson and
  Kim Christen) supplies community-defined permission/attribution metadata for exactly sacred,
  ceremonial, gender-restricted, and seasonally-restricted material; the Library of Congress already
  uses TK Labels. (https://localcontexts.org/labels/traditional-knowledge-labels/,
  https://www.nature.com/articles/s41597-021-00892-0)
- **ATU + Thompson Motif-Index** as the classification spine is the correct scholarly interoperability
  choice.
- **`origin: uncertain` as a first-class honest value**, host-independent persistent IDs (w3id/PURL),
  CC-BY-SA segregation, and CI provenance/attribution linters are all sound.
- **Honesty about the missing steward** (`verifiedNeed=false` throughout) is consistent with the Hee-Lee Oss
  "delivered ≠ merged" bar.

**Gaps, errors, and under-specifications (ranked)**

1. **The two named flagship sources are partly mis-characterized — a copyright-gate self-test the plan
   currently fails.**
   - **D.L. Ashliman's "Folktexts"** is repeatedly cited (PLAN §Data, References) as a candidate PD
     source. But Ashliman's site is **explicitly copyrighted** ("© D. L. Ashliman, University of
     Pittsburgh, 1996–2022"); his English translations and editorial framing are his own protected
     work, *not* PD. (https://sites.pitt.edu/~dash/folktexts.html,
     https://archives.internetscout.org/r19512/folklore_and_mythology_electronic_texts) The corpus may
     use the *underlying PD primary editions* Ashliman cites, but must **never** reproduce his
     translations/headnotes. The plan should add Ashliman to a "reference index, not a text source"
     list — and the fact that the plan's own example source fails Gate 1 proves the gate is necessary
     and should be used as the canonical training example for reviewers.
   - **sacred-texts.com (ISTA)** is described as "predominantly PD; verify each," which is accurate but
     understated. ISTA itself warns it has *no authority to clear copyright on PD material*, and that
     non-PD additions are "© John Bruno Hare, All Rights Reserved." Its OCR/markup also carries its own
     compilation claims. Treat ISTA strictly as a *pointer* to source editions, verified independently.
     (https://sacred-texts.com/cnote.htm) Doubly fraught: a "sacred texts" archive is precisely where
     Gate 2 (sacred/restricted material) bites hardest — sourcing a folktale *from* an archive of
     religious/sacred texts should auto-trigger cultural review.

2. **The ATU/Motif-Index citability problem is flagged as an open question but not resolved, and it is
   load-bearing.** The current **Uther (2004)** ATU index and the standard Thompson Motif-Index are
   **under copyright and largely print-only**; the Aarne (1910)/Thompson (1928/1961) earlier editions
   have different status. (https://en.wikipedia.org/wiki/Aarne%E2%80%93Thompson%E2%80%93Uther_Index)
   You can *use ATU type numbers* (facts/short labels — not protectable) and *cite* the index, but you
   must **not** reproduce Uther's descriptive prose or the index's selection/arrangement wholesale.
   The plan should state plainly: ATU numbers + your own descriptions = fine; copying index entries =
   not. This deserves promotion from "open question" to a Gate-1 sub-policy.

3. **Indigenous Data Sovereignty needs a *positive* engagement model, not only an exclusion rule.** The
   plan's default — exclude-and-flag when uncertain — is correct and safe, but risks becoming a
   *de-facto erasure* of exactly the under-represented cultures the project says it centers (it could
   end up a corpus of safe European literary fairy tales). Add: (a) an explicit, resourced pathway for
   communities to *opt in* and govern their own material (consent + compensation + ongoing control,
   per CARE's "Authority to Control"); (b) recognition that **community consent can be conditional and
   revocable** — the schema needs a takedown/embargo mechanism, not just a publish flag. Mukurtu (built
   2007 with the Warumungu community; fine-grained cultural-protocol access tiers) is the reference
   model for "share *with* protocols," not "publish or exclude." (https://mukurtu.org/about/)

4. **"Community-open evidence" is under-defined and is the project's highest-risk judgment call.** What
   counts as a community having "openly published it for reuse"? A single community member posting a
   story online is *not* community consent. The plan needs a documented evidentiary standard
   (who speaks for a community; collective vs individual authority; what provenance of consent looks
   like) before M1, or reviewers will improvise inconsistently.

5. **Colonial framing is named but the remediation is thin.** Most PD 19th-c collections (Lang's
   *Fairy Books*, Jacobs, Hearn, many missionary/ethnographer compilations) are PD precisely *because*
   they are old — and they are saturated with colonial framing, bowdlerization, racialized language,
   and uncredited/flattened origins. (https://en.wikipedia.org/wiki/Andrew_Lang; Lang treated tales as
   "authorless... belong to no one and thus available to anyone" —
   https://www.erudit.org/en/journals/ravon/2013-n64-ravon01452/1025670ar/) The plan should require a
   **provenance/critical note field** recording the collector's stance and known distortions, and
   should prefer the *earliest attributable source culture* over the colonial intermediary in
   `culturalAttribution` (with the intermediary recorded as collector, not origin).

6. **Scope risk: 300 tales / 25 regions / 10 languages in 12 months with a human dual-gate is
   aggressive** given that copyright + cultural + accuracy review are all human bottlenecks and several
   reviewer seats are unfilled. The plan acknowledges a throughput ceiling; it should set a *floor*
   too — better to ship 80 impeccably-gated tales than 300 thinly-reviewed ones. Consider reframing the
   M3 target as a *quality-rate* primary and *count* secondary.

7. **Minor:** Project Gutenberg's underlying texts are PD, but the **PG trademark/license** restricts
   redistribution of PG-branded/marked files (esp. commercially); strip the PG header/license and work
   from the underlying PD edition, or source the edition directly. Worth a one-line note in the
   allowlist policy.

**Net:** the plan's *architecture* is correct; the gaps are in *operationalizing judgment* (consent
evidence, colonial-framing remediation, ATU rights, the Ashliman/ISTA mischaracterizations) and in
making the exclusion rule not collapse into erasure.

---

## 2. Competitive landscape (researched, cited)

| Project | What it is | Strengths | Weaknesses / gap vs. this plan |
| --- | --- | --- | --- |
| **Project Gutenberg** (folklore subset) | ~70k PD e-texts incl. Grimm/Lang/Jacobs/Hearn | Massive, genuinely PD, stable | Unstructured prose; no ATU/motif; no cultural attribution or consent layer; colonial editions unannotated; PG trademark license on marked files. (gutenberg.org) |
| **D.L. Ashliman — Folktexts** | Curated, ATU-organized folktale texts + essays, Univ. Pittsburgh | Excellent ATU organization; scholarly; free to read | **Copyrighted to Ashliman** (not reusable); link-rot risk; single maintainer; not a reusable dataset. (https://sites.pitt.edu/~dash/folktexts.html) |
| **Internet Sacred Text Archive (sacred-texts.com)** | ~1,700 PD religion/myth/folklore books | Broad; long-standing | Mixed rights ("no authority to clear PD"; some © John Bruno Hare); OCR-era markup; sacred-material sensitivity unaddressed. (https://sacred-texts.com/cnote.htm) |
| **Wikisource** | Crowd-transcribed PD/CC-BY-SA texts | Real provenance to scans; community-maintained; *English Fairy Tales* etc. present | CC-BY-SA share-alike contaminates CC0/CC-BY reuse; uneven coverage; no ATU/consent layer. (https://en.wikisource.org/wiki/English_Fairy_Tales) |
| **StoryWeaver (Pratham Books)** | 60k+ books, ~300+ languages, **CC-BY-4.0**, translate/remix tools | Best-in-class openness + multilingual tooling + scale; includes folktales | Created/retold modern content, not provenance-traced PD source editions; no ATU/motif index; no Indigenous-consent gate. (https://storyweaver.org.in/en/prathambooks) |
| **African Storybook (Saide)** | 3,800 originals + 7,200 translations, 236 African languages, open-licensed | Community-authored; deep African-language reach; literacy-focused | New leveled readers, not a sourced folktale corpus; little ATU/scholarly metadata. (https://en.wikipedia.org/wiki/African_Storybook) |
| **Global Storybooks (UBC)** | Portal re-serving ASb/StoryWeaver in 50+ languages, 40+ country sites | Great delivery/UX; multilingual | Aggregator of others' content; not a provenance/consent corpus. (https://globalstorybooks.net/faq/) |
| **WorldStories (KidsOut)** | 175 retold + original stories in 32 UK-community languages | Volunteer-translated; UK-classroom fit | Small; retellings without source-edition provenance; EULA-restricted (not openly licensed). (https://worldstories.org.uk/about) |
| **University folklore archives / HathiTrust** | Scanned indexes (Thompson Motif-Index), academic guides | Authoritative; scholarly | Access-gated/print; not reusable datasets; no consent layer. (https://guides.library.harvard.edu/folk_and_myth/indices) |
| **Mukurtu CMS (WSU)** | Indigenous heritage CMS with cultural-protocol access tiers + TK Labels | The gold standard for *consent-governed* sharing | A platform communities self-host, not an open cross-cultural corpus; complementary, not competing. (https://mukurtu.org/about/) |
| **UNESCO ICH — Oral traditions domain** | Convention + Representative/Urgent lists; safeguarding "as process not product" | Authoritative legitimacy; community-centric ethos | Policy/inventory, not a reusable text corpus; explicitly wary of fixing oral tradition into "products." (https://ich.unesco.org/en/oral-traditions-and-expressions-00053) |

**Synthesis:** the field splits into (a) *big PD text dumps* with no structure/attribution/consent
(Gutenberg, ISTA, Wikisource, Ashliman) and (b) *beautifully open, multilingual retelling platforms*
with no PD-source-provenance or ATU layer (StoryWeaver, ASb, Global Storybooks, WorldStories), plus
(c) *consent-governance tooling* (Mukurtu, Local Contexts) and *policy bodies* (UNESCO) that nobody has
fused with an open corpus. **No one occupies the intersection.**

---

## 3. Gaps we can fill

- **The intersection itself:** an open, *structured*, *provenance-traced*, *ATU-classified*,
  *consent-respecting*, *multilingual* folktale corpus. Each competitor has 2–3 of these properties;
  none has all.
- **Machine-checkable per-tale provenance chain** (source edition → rights basis → translation/
  retelling lineage), absent everywhere — Gutenberg/ISTA/Ashliman give prose, not data.
- **A cultural-consent layer wired into an *open* corpus.** Mukurtu does consent but for self-hosted
  community archives; StoryWeaver does openness but no consent gate. Fusing TK Labels/CARE into a
  cross-cultural open dataset is genuinely novel.
- **ATU/motif cross-variant linking across cultures** as reusable data (Wikidata-reconciled), so a
  teacher can find every "Cinderella/ATU 510A" variant with attribution — no open dataset does this.
- **De-colonial annotation:** recording collector stance and known distortions alongside the text, and
  attributing to the *origin culture* not the colonial collector.
- **Clean, rights-clear *source* text for downstream pipelines** (literacy, decodable readers,
  read-aloud audio, translation) — StoryWeaver gives finished readers, not a corpus other open projects
  can build on with provenance intact.
- **Low-resource-language source texts the community can translate and *own* (CC-BY)** with provenance,
  rather than orphaned retellings.

---

## 4. Differentiators to win

1. **Dual-gate provenance is the moat.** "Every tale is *both* legally verified (per edition) *and*
   culturally cleared, with a machine-readable chain" is a claim no competitor can currently make. This
   is the single strongest differentiator.
2. **Consent-governed *and* open.** Adopt Local Contexts TK Labels + CARE in an openly-licensed corpus
   — pairing Mukurtu-style protocols with StoryWeaver-style openness.
3. **Scholarly interoperability:** ATU + motif + Wikidata reconciliation makes the corpus a research
   instrument, not just a reading site.
4. **De-colonial attribution by design:** origin-culture-first attribution + collector-stance notes
   directly answers the field's biggest ethical failure.
5. **Infrastructure, not destination:** JSON/JSON-LD + persistent IDs positions it as the upstream
   corpus for the whole Hee-Lee Oss open-content portfolio.
6. **Radical honesty:** `origin: uncertain`, recorded distortions, and `verifiedNeed=false` build the
   trust that wins institutional stewards.

---

## 5. Claude API leverage (and where Claude must NOT decide)

**High-value, human-reviewed uses:**
- **Structuring/normalization:** turn messy OCR/prose PD editions into the tale schema (split tales,
  extract titles/aka, normalize YAML front-matter) — assistive, every field human-verified.
- **OCR post-correction** against the source image (flag-on-doubt; never silently "fix").
- **Translation *drafts*** for new CC-BY translations and child retellings — always back-checked by a
  fluent human; Claude produces a draft + a change-note candidate, not a publishable text.
- **ATU/motif *candidate* classification** — suggest ATU type + motifs with rationale and confidence,
  for a human to confirm; great at surfacing cross-cultural variants to link.
- **Metadata enrichment:** reading-level/age estimates, content-warning candidates, BCP-47 tags,
  draft critical/colonial-framing notes for reviewer editing.
- **Reviewer tooling:** anti-laundering spot-check (flag suspiciously modern phrasing vs the cited PD
  edition); provenance/attribution completeness pre-checks before CI.
- **Pipeline/CI code** (linters, exporters, JSON-LD shaping) — standard donated-lane coding help.

**Where Claude must NOT be the decider (hard boundaries, mirror the plan's refusals):**
- **Cultural ownership / consent** — community-governed, never model-inferred. Claude may *draft a
  question for the community*; it must never *grant* permission.
- **Sacred/restricted determination** — default exclude-and-flag to a human cultural reviewer; the
  model must not reclassify restricted material as publishable.
- **Final attribution / origin** — no guessed origins; `origin: uncertain` over a plausible-sounding
  fabrication. Claude must not invent a source culture.
- **No fabricated folklore or provenance** — Claude must never generate a "traditional tale," a missing
  source citation, or a plausible-but-unverified edition.
- **Respectful framing** — model-drafted notes are reviewed by a human with cultural competence before
  publish.
- **Copyright / license status** — Claude flags and drafts the rights analysis; a named human copyright
  reviewer makes the call. The model's guess of "this looks PD" is never the gate.

Reference for current model IDs/pricing/caching when implementing: the `claude-api` skill (do not rely
on memory).

---

## 6. Ten concrete optimizations

1. **Reclassify Ashliman and ISTA in the allowlist policy** as *reference indexes / pointers*, not text
   sources; write the Ashliman case up as the canonical Gate-1 training example for reviewers.
2. **Add an ATU-rights sub-policy:** use ATU type numbers + your own descriptions; never reproduce
   Uther (2004) entry prose or the index's arrangement. Resolve the open question now.
3. **Add `criticalNote` / `collectorStance` schema fields** capturing colonial framing, bowdlerization,
   and known distortions; attribute origin-culture-first, collector-second.
4. **Define a written "community-open evidence" standard** (who may consent, collective vs individual
   authority, provenance of consent) before M1 — the highest-variance reviewer judgment.
5. **Add embargo/takedown/revocation mechanics** to the schema and ID layer (consent can be conditional
   and revocable; persistent IDs must support tombstoning) — CARE "Authority to Control."
6. **Adopt TK Labels machine-readably** via the Local Contexts Hub API/Notices, not just prose mention,
   so labels travel with the JSON-LD. (https://support.datacite.org/docs/local-contexts-notices-and-labels)
7. **Set a quality *floor* alongside the count target:** make impeccable gating the primary M3 metric,
   tale-count secondary; codify the throughput ceiling as a hard intake throttle.
8. **Build a Claude-assisted but human-final ATU classifier + variant-linker** with confidence scores
   and a "needs human" queue; reconcile to Wikidata (CC0) IDs.
9. **Reconcile cultures/regions to authority files** (Wikidata, ISO 639-3/Glottolog for languages,
   not just BCP-47) to make low-resource languages first-class and avoid mis-coding.
10. **Strip Project Gutenberg trademark headers / work from the underlying PD edition**, and prefer
    Standard Ebooks (CC0 typesetting) or direct edition scans where available; record the exact scan.

---

## 7. Parallel & perpendicular spin-offs

- **`folktale-corpus-atu` (perpendicular, research infra):** the ATU/motif-indexed, Wikidata-reconciled
  variant-graph as a standalone open dataset + browsable explorer — a citable research instrument for
  folklorists, decoupled from the reading UX.
- **MCP server (`folktales-mcp`):** expose the corpus (query by ATU type, culture, language, reading
  level; fetch provenance; respect TK-Label access tiers) so other agents/apps consume it safely —
  with restricted/embargoed material *never* served. Natural fit for the Hee-Lee Oss ecosystem.
- **Ties to siblings (parallel):**
  - `open-childrens-books` — illustrated, rights-cleared editions built on this clean text (the plan
    already defers illustration there).
  - `public-domain-translations` — shares the per-edition copyright-verification engine and reviewer
    workflow; co-develop the allowlist tooling.
  - `read-aloud-audio` — narrate the cleared tales (consent gate must extend to *voicing* sacred-
    adjacent material).
  - `heritage-recipes-open` — same dual-gate pattern (PD + cultural-ownership/consent) applied to
    traditional foodways; share the TK-Label/CARE governance module wholesale.
  - `literacy-from-zero` / `decodable-readers` — leveled/decodable derivations from the corpus.
- **Shared module to extract:** a reusable **"dual-gate governance kit"** (per-edition copyright
  analysis schema + TK-Label/CARE consent workflow + provenance linters) usable by every Hee-Lee Oss
  cultural-heritage project. This is arguably the most valuable perpendicular asset the project creates.

---

## 8. Open questions

- **Steward/partner** (blocks "shipped") — who adopts/hosts/cites? Library digital-collections team,
  folklore society, university DH program, or a language-revitalization org?
- **Consent evidentiary standard:** who speaks for a community; how is collective consent documented;
  how (and whether) are community partners compensated? (Plan flags compensation as open — it is
  central, not peripheral.)
- **ATU/Motif-Index citable editions:** which editions can be cited/used without rights issues, and how
  deep to classify? (Promote to a decided policy.)
- **Erasure vs. caution:** how to avoid the exclude-and-flag default quietly producing a
  Euro-centric-literary corpus — what positive opt-in pipeline funds under-represented inclusion?
- **Variant representation:** how to present multiple cultural variants of one ATU type without
  implying a "real"/canonical version?
- **Revocation/embargo:** what is the takedown SLA and tombstone behavior when a community withdraws
  consent post-publication?
- **Target languages** for new CC-BY translations (driven by which partner communities sign on).
- **Reviewer staffing & SLA:** copyright, cultural, and per-language reviewer seats are all unfilled;
  what is the realistic throughput, and the floor below which intake throttles?

---

### Summary (250–350 words)

`world-folktales-open` aims at a genuinely empty intersection. The field divides into **big public-
domain text dumps with no structure, attribution, or consent** (Project Gutenberg, the Internet Sacred
Text Archive, Wikisource, D.L. Ashliman's Folktexts) and **beautifully open, multilingual *retelling*
platforms with no PD-source provenance or scholarly index** (Pratham's StoryWeaver, African Storybook,
Global Storybooks, WorldStories) — plus consent-governance tooling (Mukurtu, Local Contexts) and policy
bodies (UNESCO ICH) that nobody has fused with an open corpus. **Top three competitors: StoryWeaver**
(scale + CC-BY + translation tooling, but modern retellings not traced PD editions), **Project
Gutenberg** (real PD scale, zero structure/consent), and **D.L. Ashliman's Folktexts** (best ATU
curation, but copyrighted and not reusable). The **single strongest differentiator** is the
**dual-gate, machine-readable provenance chain**: every tale verified per-edition for copyright *and*
cleared for cultural permission — a claim no competitor can make.

**Top three Claude-API ideas:** (1) structure/normalize messy OCR'd PD editions into the tale schema +
OCR post-correction; (2) draft new CC-BY translations and child retellings *with* change-notes, always
human back-checked; (3) candidate ATU/motif classification + cross-cultural variant linking
(Wikidata-reconciled) with confidence scores and a human-confirm queue. Claude must **never** decide
cultural ownership/consent, sacred/restricted status, final attribution/origin, or copyright status,
and must never fabricate folklore or provenance.

**Two most important plan-correctness findings:** (1) **the project's own flagship sources fail Gate 1
as written** — Ashliman's Folktexts are *copyrighted to him* and sacred-texts.com disclaims any
authority to clear PD; both must be reclassified as reference *pointers*, not text sources. (2) The
**cultural-ownership / sacred-material dimension needs a positive, governed engagement model**, not only
an exclusion rule: define a real "community-open evidence" standard, adopt TK Labels machine-readably,
and add embargo/revocation mechanics (CARE "Authority to Control") — otherwise exclude-and-flag quietly
erases the under-represented cultures the project exists to center.
