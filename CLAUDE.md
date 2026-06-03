# CLAUDE.md

This repository is an **LLM-maintained research wiki on single-cell foundation models (scFMs)**, usable as an Obsidian vault and deployable as a Quartz site.

## Read this first

**All maintenance instructions live in [`AGENTS.md`](AGENTS.md).** Read it fully before creating or editing any page — especially §0 (non-negotiable principles) and §3 (paper ingestion workflow).

## Quick orientation

- Content lives in `content/`. See `content/index.md` (home), `content/catalog.md` (master index), `content/log.md` (edit log).
- Templates are in `content/90-Meta/templates/`. Use them; do not freelance page structure.
- Folders are numbered by kind: `00-Sources`, `10-Summaries`, `20-Models`, `30-Concepts`, `40-Topics`, `50-Notes`, `60-Datasets`, `70-Benchmarks`, `80-Comparisons`, `90-Meta`.

## The five rules you will most often break

1. **Don't overclaim.** Cite or mark `unclear` / `needs verification`. A correct "unclear" beats a confident error.
2. **Separate** zero-shot vs fine-tuning vs supervised perturbation prediction.
3. **Distinguish** embedding shift vs classifier-score shift vs true transcriptome-level prediction.
4. **State the input representation** (gene identity / rank-based / binned / raw expression / condition token / metadata / multi-omic) and **how perturbation data were used** (pretrain / fine-tune / eval / not used).
5. **General scFMs ≠ perturbation-specific models** (GEARS, CPA, scGen).

## Ingesting a paper

If the user gives you First author / Title / Year / Venue / Section / Model / Main task, follow `AGENTS.md` §3: verify the paper exists and matches, then create the summary (24 fields) and propagate to catalog, log, model/concept/topic/dataset/benchmark/comparison pages. If you cannot confidently identify the paper, **do not guess** — add it to `content/50-Notes/unresolved-paper-requests.md`.

## Conventions

- Plain Markdown only. Obsidian wikilinks `[[like this]]`. YAML frontmatter on every page (see any template).
- Keep filenames stable; use frontmatter `aliases:` so multi-word wikilinks resolve.
- After any change, bump `updated:` and add a `log.md` entry.
