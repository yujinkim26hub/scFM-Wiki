---
title: Log
aliases: [log, changelog]
type: note
tags: [log, scfm]
status: draft
updated: 2026-06-03
---

# Log

Chronological record of ingestions and substantive edits. **Prepend** new entries (newest first). Each entry: date, what changed, pages touched.

---

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
