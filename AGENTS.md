# AGENTS.md — instructions for the LLM maintaining scFM-Wiki

This file tells any LLM agent (Claude Code, or another) how to maintain this wiki. Read it fully before editing. `CLAUDE.md` points here.

This is a **research wiki on single-cell foundation models (scFMs)**. Your job is to keep it accurate, well-linked, and honest about uncertainty. Accuracy and epistemic discipline matter more than completeness or fluency.

---

## 0. Non-negotiable principles

1. **Do not overclaim.** Never write that a model "can do X" unless a cited source supports it. Prefer "reported to", "the authors report", "benchmarked on".
2. **Separate capability classes.** Keep distinct: (a) **zero-shot** use of frozen embeddings, (b) **fine-tuning** a pretrained model with a task head, (c) **supervised perturbation prediction** trained on perturbation data.
3. **Distinguish output types.** A *cell-embedding shift*, a *classifier-score shift*, and a *true transcriptome-level (gene expression) prediction* are different claims. Say which one a model produces.
4. **Be explicit about input representation.** State whether a model uses gene identity tokens, rank-based expression ordering, binned expression values, raw/continuous expression, condition/perturbation tokens, metadata tokens, or multi-omic input.
5. **Be explicit about perturbation data use.** For any model: were perturbation data used for **pretraining**, **fine-tuning**, **evaluation only**, or **not used**?
6. **Distinguish general scFMs from perturbation-specific models.** Geneformer, scGPT, scFoundation, scBERT, scMamba, CellPLM, scPRINT, UCE, CellFM, GeneCompass are general scFMs. GEARS, CPA, scGen are perturbation-specific models (not pretrained foundation models in the same sense).
7. **Do not infer biology beyond the source.** No clinical or mechanistic conclusions the paper does not make.
8. **Mark uncertainty.** Use `unclear` or `needs verification` inline whenever you are not confident. Never invent numbers, dataset names, or architectural details.
9. **Compare on explicit criteria**, never with bare "better than" claims.
10. Plain, Obsidian-readable Markdown only. No HTML, no vector DB, no heavy automation.

When unsure whether something is true, **leave it marked uncertain rather than guessing.** A correct "unclear" is worth more than a confident error.

---

## 1. Repository map

| Folder | Holds | Page template |
|---|---|---|
| `00-Sources/` | One metadata note per source (paper/preprint/dataset doc) | `90-Meta/templates/source-template.md` |
| `10-Summaries/` | Structured paper summaries (the 24-field template) | `90-Meta/templates/paper-summary-template.md` |
| `20-Models/` | One page per model | `90-Meta/templates/model-template.md` |
| `30-Concepts/` | Core concepts | `90-Meta/templates/concept-template.md` |
| `40-Topics/` | Cross-cutting topics | `90-Meta/templates/topic-template.md` |
| `50-Notes/` | Working notes; `unresolved-paper-requests.md` | — |
| `60-Datasets/` | Datasets | `90-Meta/templates/dataset-template.md` |
| `70-Benchmarks/` | Benchmark tasks | `90-Meta/templates/benchmark-template.md` |
| `80-Comparisons/` | Cross-model comparisons by shared criteria | `90-Meta/templates/comparison-template.md` |

`content/index.md` is the home map. `content/catalog.md` is the master index. `content/log.md` is the chronological edit log.

---

## 2. File & link conventions

- **Filenames** mirror the page title, lower-kebab-case for concepts/topics (`gene-embedding.md`), and the model's canonical capitalization for models (`scGPT.md`, `Geneformer.md`). Obsidian wikilinks resolve by basename regardless of folder.
- **Wikilinks** use the display title: `[[scGPT]]`, `[[gene embedding]]`, `[[in silico perturbation]]`. If the filename differs from the link text, use an alias in the page's frontmatter `aliases:` so the link resolves. Keep aliases for every multi-word concept (e.g. file `gene-embedding.md` has `aliases: [gene embedding, gene embeddings]`).
- **Frontmatter** (YAML) on every page:
  ```yaml
  ---
  title: <display title>
  aliases: [<alt names / link text>]
  type: model | concept | topic | dataset | benchmark | comparison | summary | source | note
  tags: [scfm, ...]
  status: stub | draft | reviewed
  updated: YYYY-MM-DD
  ---
  ```
- **Tags** are lower-case, hyphenated: `#scfm`, `#perturbation`, `#zero-shot`, `#batch-correction`, `#neuro`, `#benchmark`, `#dataset`, `#transformer`, `#needs-verification`.
- Every page should link to at least one concept and the relevant model(s). Avoid orphan pages.
- Use `status: stub` for starter pages that have not yet been filled from primary sources; `draft` once content is added; `reviewed` only after a human confirms.

---

## 3. Paper ingestion workflow

When the user provides a paper request in this form:

```
First author:
Title:
Year:
Journal / Venue:
Section:
Model name (if applicable):
Main task:
```

do the following, in order:

### 3.1 Identify & verify
1. Search the web for the paper (title + first author + year + venue). Prefer DOI, the publisher page, PubMed, or the official preprint (bioRxiv/arXiv).
2. **Verify identity**: the title, first author, year, and venue must match. If a model name was given, confirm the paper actually introduces or substantially uses it.
3. **If you cannot confidently identify the paper, STOP.** Do not invent a summary. Append an entry to `content/50-Notes/unresolved-paper-requests.md` under "needs verification" with everything the user gave you and what you searched. Tell the user what is missing.

### 3.2 Create the source note
Create `00-Sources/<firstauthor-year-shortslug>.md` from `source-template.md` with bibliographic metadata, DOI/URL, and links out to the summary.

### 3.3 Create the summary
Create `10-Summaries/<firstauthor-year-shortslug>.md` from `paper-summary-template.md`. **Every summary must contain all 24 fields** (see §4). Fill only what the source supports; mark the rest `unclear` / `not applicable` / `needs verification`. Do not pad with speculation.

### 3.4 Propagate the update
After the summary exists, update:
- **`catalog.md`** — add the paper row and any new model/concept/dataset/benchmark rows.
- **`log.md`** — prepend a dated entry describing what was ingested and what pages changed.
- **Model page(s)** in `20-Models/` — if the paper introduces or evaluates a model, update Original paper, architecture, capabilities, benchmarks, etc. Add the paper to "Related papers".
- **Concept pages** in `30-Concepts/` — add the paper as an example/reference where it advances a concept.
- **Topic pages** in `40-Topics/` — add to the relevant topic (e.g. disease, perturbation).
- **Dataset pages** in `60-Datasets/` — add datasets the paper introduces or uses; create new dataset pages if needed.
- **Benchmark pages** in `70-Benchmarks/` — add tasks/metrics the paper reports.
- **Comparison pages** in `80-Comparisons/` — add a row per relevant criterion table, with the source paper as evidence.
- **Connect**: add wikilinks between the new paper and related models/papers/concepts in both directions.

### 3.5 Report
Summarize to the user: what was created/updated, what was left `unclear`, and any open questions.

---

## 4. The 24-field paper summary

Every `10-Summaries/` page includes these numbered fields in order (see `paper-summary-template.md`):

1. Citation
2. Core question
3. Prior studies
4. Limitations of prior studies
5. What this study did
6. Main results of this study
7. Limitations of this study
8. Methods
9. Model architecture
10. Input data type
11. Tokenization or encoding strategy
12. Pretraining data
13. Fine-tuning strategy (if applicable)
14. Main tasks evaluated
15. Benchmark datasets and metrics
16. Perturbation analysis (if applicable)
17. Batch correction or data integration (if applicable)
18. Interpretability or biological insight
19. Relevance to single-cell foundation models
20. Relevance to disease biology
21. Connection to other papers or models
22. Related concepts
23. Open questions
24. Tags

Fields 13, 16, 17 may be "not applicable" — say so explicitly rather than omitting them.

---

## 5. Model pages

Use `model-template.md`. Organize around the workflow **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use**. Always make crystal clear: what goes **in**, how it is **represented**, what comes **out**, and what the output may or may not be interpreted as biologically. For capabilities, fill the Input/Processing/Output flow before anything else.

## 6. Comparison pages

Compare models on a **single shared criterion** per page (architecture, input format, tokenization, pretraining data, supported tasks, zero-shot, fine-tuning, perturbation, batch correction, benchmarks, disease validation, etc.). Use a table with columns: **Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty.** Do **not** rank models or declare a winner. Direct model-vs-model pages (`[[Geneformer vs scGPT]]`) are created **only later**, once both model pages and the relevant summaries contain enough verified detail.

## 7. Style

- Be concise. Favor tables and short statements over prose.
- Cite inline as `(First author, Year)` linking to the summary page, e.g. `([[Theodoris-2023-geneformer|Theodoris 2023]])`.
- Keep one fact per sentence where capability claims are involved.
- Never delete sourced content to "tidy up"; mark it instead.
- When you finish a task, update `updated:` frontmatter and `log.md`.
