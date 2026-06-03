---
title: Log
aliases: [changelog]
type: note
tags: [log, scfm]
status: draft
updated: 2026-06-03
---

# Log

Chronological record of ingestions and substantive edits. **Prepend** new entries (newest first). Each entry: date, what changed, pages touched.

---

## 2026-06-03 — Fix flattened section URLs for source/summary pages

- **Bug:** the UCE summary/source published at `/10-Summaries/…` and `/00-Sources/…` correctly, but inbound links (incl. [[catalog|Catalog]]) pointed at flattened **root** URLs (`/rosen-…`). Cause: the pages aliased themselves to their own filename slug; Quartz emits each alias as a root-level redirect, and with `shortest` link resolution `[[wikilinks]]` resolved to that flat root slug.
- **Fix:** removed the self-referential aliases from [[rosen-2023-universal-cell-embeddings]] and [[rosen-2023-universal-cell-embeddings-source]]. Links now resolve by basename to the real section paths. Updated `paper-summary-template`/`source-template` (no self-alias) and [[AGENTS]] §2 to prevent recurrence.
- Verified locally (Quartz v4): pages publish at `/10-Summaries/…` and `/00-Sources/…`, root flat stubs gone, catalog link uses the section path.

## 2026-06-03 — Ingested: Rosen 2023 (UCE)

- Ingested **[[rosen-2023-universal-cell-embeddings|Rosen et al. 2023 — Universal Cell Embeddings (UCE)]]**, bioRxiv, DOI 10.1101/2023.11.28.568918. Identity verified (title, first author Yanay Rosen, year, venue, DOI).
- Created source note [[rosen-2023-universal-cell-embeddings-source]] and the 24-field summary [[rosen-2023-universal-cell-embeddings]] (`status: reviewed`).
- Updated [[catalog|Catalog]] (added the paper row) and the model page [[UCE]] (verified architecture = 33-layer/~650M transformer; ESM2 protein-embedding gene encoding + expression-weighted "cell sentence"; masked-binary pretraining objective; ~36M cells / 8 species; zero-shot, "not intended to be finetuned"; scIB integration eval on Tabula Sapiens v2 & Human Brain Cell Atlas; no perturbation).
- Cross-linked concept pages: [[cell embedding]], [[gene embedding]], [[single-cell foundation model]], [[zero-shot prediction]]; and comparison rows for UCE where now evidence-backed.
- Epistemic notes: UCE output is a **cell embedding** (not transcriptome-level / not perturbation prediction); exact embedding dimension and scIB scores left `needs verification`.

## 2026-06-03 — Fix blank Catalog/Log pages; exclude templates from site

- **Bug:** [[catalog|Catalog]] and [[log|Log]] rendered as blank white pages. Cause: `catalog.md`/`log.md` listed their own slug as an alias (`aliases: [catalog, …]` / `[log, …]`). Quartz emits alias redirects at the site root, so for these root-level pages the redirect overwrote the real page with a self-referential `<meta refresh>` loop. (Subfolder pages like `20-Models/Geneformer` were unaffected — their root-level alias redirect sits at a different path than the real page.)
- **Fix:** removed the self-referential aliases (`catalog`, `log`). Links still resolve by filename slug; pages now render real content. `catalog.md`/`log.md` stay at the content root.
- **Site cleanup:** `deploy.yml` now removes `90-Meta/templates` from the *copied* Quartz content (templates remain in the repo / Obsidian vault), so placeholder pages like `<concept>.html` are no longer published.
- Verified locally (Quartz v4): `catalog.html`/`log.html` contain real content, title stays "scFM-Wiki", no new unresolved wikilinks.

## 2026-06-03 — Fix Quartz Pages build

- Quartz's default branch moved to **v5 (5.0.0)**, which expects a generated `.quartz/` directory; a bare clone-and-build failed with `Could not resolve "../../.quartz/plugins"`.
- Pinned `.github/workflows/deploy.yml` to Quartz **v4** (`ref: v4`, 4.5.2), which builds directly from a clone. Set `baseUrl` for the project-page subpath; upload `quartz/public`.
- Verified locally: `npx quartz build` emits the full site (95 inputs → 433 files) with no errors.
- Gave the 8 page templates a valid `updated:` date to silence Quartz date-parse warnings.

## 2026-06-03 — Initial scaffold

- Created the vault structure: `00-Sources` … `90-Meta/templates`.
- Wrote system docs: `README.md`, `AGENTS.md`, `CLAUDE.md`.
- Wrote hub pages: [[index]], [[catalog|Catalog]], [[log|Log]].
- Added page templates (paper summary 24-field, model, concept, topic, dataset, benchmark, comparison, source).
- Created **starter (stub) pages**:
  - 12 models: [[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[scMamba]], [[CellPLM]], [[scPRINT]], [[UCE]], [[GeneCompass]], [[GEARS]], [[CPA]], [[scGen]].
  - 20 concepts, 8 topics, 8 datasets, 8 benchmarks, 18 comparison pages.
  - [[unresolved-paper-requests]] note.
- Added Quartz GitHub Pages deploy workflow (`.github/workflows/deploy.yml`).
- **Status:** all model/concept/etc. pages are `stub` — populated from general knowledge as scaffolding, to be verified and expanded via the paper-ingestion workflow. No paper summaries ingested yet.

> Going forward, every paper ingested via the [[AGENTS]] workflow gets an entry here.
