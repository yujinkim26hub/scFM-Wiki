# scFM-Wiki

An **LLM-maintained research wiki** on **single-cell foundation models (scFMs)** and their biomedical applications.

This repository is three things at once:

1. An **Obsidian vault** — open the `content/` folder as a vault and the wikilinks, graph view, and templates work immediately.
2. A **Markdown-based, LLM-maintained research wiki** — pages are plain Markdown, designed to be created and updated by an LLM agent (see `AGENTS.md` / `CLAUDE.md`) following a strict paper-ingestion workflow.
3. A **[Quartz](https://quartz.jzhao.xyz/) website** deployable to **GitHub Pages** — `content/` is the Quartz content root.

The conceptual model follows Karpathy's "LLM Wiki" idea: a living, hyperlinked knowledge base that an LLM keeps current, where every claim is traceable to a source and uncertainty is stated rather than hidden.

> ⚠️ **Epistemic policy.** This wiki deliberately *avoids overclaiming*. Model capabilities are separated into zero-shot, fine-tuning, and supervised perturbation prediction; embedding shifts are distinguished from true transcriptome-level prediction; and anything uncertain is marked `unclear` or `needs verification`. See [Principles](#principles).

---

## Scope

Single-cell and cell foundation models, virtual cell models, and the surrounding biology and methodology: single-cell omics (scRNA-seq, snRNA-seq, scATAC-seq, multi-omics), gene/cell embeddings, gene regulatory networks, cell state and cell-state transitions, cell type annotation, batch correction and data integration, atlas mapping, in silico perturbation and perturbation prediction (Perturb-seq, CROP-seq, CRISPR), benchmarking, zero-shot/fine-tuning/transfer learning, tokenization and encoding strategies, interpretability, and disease biology with an emphasis on neurological / neurodegenerative / neurodevelopmental / neuropsychiatric disease.

Models tracked include Geneformer, scGPT, scFoundation, scBERT, scMamba, CellPLM, scPRINT, UCE, CellFM, GeneCompass, and the perturbation-specific models GEARS, CPA, and scGen — plus others as they are added.

---

## Repository layout

```
content/
├── index.md                 # wiki home / map of contents
├── catalog.md               # master index of every page (models, papers, concepts…)
├── log.md                   # chronological ingestion / edit log
├── 00-Sources/              # raw source metadata (one note per paper/source)
├── 10-Summaries/            # structured paper summaries (24-field template)
├── 20-Models/               # one page per model
├── 30-Concepts/             # core concepts (gene embedding, zero-shot, …)
├── 40-Topics/               # cross-cutting topics (scFMs for neurological disease, …)
├── 50-Notes/                # working notes, incl. unresolved-paper-requests.md
├── 60-Datasets/             # datasets (CELLxGENE Census, Tabula Sapiens, …)
├── 70-Benchmarks/           # benchmark tasks (cell type annotation, batch correction, …)
├── 80-Comparisons/          # cross-model comparisons by shared criteria
└── 90-Meta/templates/       # page templates
AGENTS.md                    # instructions for any LLM agent maintaining the wiki
CLAUDE.md                    # Claude Code-specific entry point (points to AGENTS.md)
```

---

## Use it as an Obsidian vault

1. Install [Obsidian](https://obsidian.md/).
2. *Open folder as vault* → select the `content/` folder.
3. Wikilinks (`[[scGPT]]`), the graph view, and the templates in `90-Meta/templates/` all work out of the box.

No plugins are required. Optional but nice: the **Templates** core plugin (point it at `90-Meta/templates/`) and **Dataview** if you later want query views.

---

## Add a paper (ingestion workflow)

Provide these fields to the agent (see `AGENTS.md` for the full procedure):

```
First author:
Title:
Year:
Journal / Venue:
Section:
Model name (if applicable):
Main task:
```

The agent will search for and **verify the paper identity**, then create a summary in `10-Summaries/`, and update `catalog.md`, `log.md`, and the relevant model / concept / topic / dataset / benchmark / comparison pages. If the paper cannot be confidently identified, it is **not guessed** — it is added to [`content/50-Notes/unresolved-paper-requests.md`](content/50-Notes/unresolved-paper-requests.md) as *needs verification*.

---

## Deploy as a Quartz site on GitHub Pages

`content/` is already laid out as a Quartz v4 content root. To publish:

1. Scaffold Quartz in a clone:
   ```bash
   git clone https://github.com/jackyzha0/quartz.git quartz && cd quartz
   npm i
   ```
2. Replace Quartz's `content/` with this repo's `content/` (or symlink / copy it in).
3. Configure `quartz.config.ts` (`baseUrl: "<user>.github.io/scFM-Wiki"`).
4. Build & deploy:
   ```bash
   npx quartz build
   npx quartz sync     # or use the GitHub Action below
   ```

A ready-to-use GitHub Actions workflow is provided at [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) — enable **Settings → Pages → Build and deployment → GitHub Actions**. See the workflow file's comments for the one-time setup. The wiki content is fully usable as plain Markdown / Obsidian even if you never deploy the site.

---

## Principles

1. Do not overclaim model capabilities.
2. Separate **zero-shot analysis**, **fine-tuning**, and **supervised perturbation prediction**.
3. Distinguish **cell-embedding shift**, **classifier-score shift**, and **true transcriptome-level perturbation prediction**.
4. State exactly what each model consumes: gene identity, rank-based expression, binned expression, raw expression value, condition tokens, metadata, or multi-omic input.
5. State whether perturbation data were used for **pretraining**, **fine-tuning**, **evaluation**, or **not used**.
6. Distinguish general scFMs from perturbation-specific models (GEARS, CPA, scGen).
7. Do not infer biology beyond what a paper supports.
8. Mark uncertain information `unclear` or `needs verification`.
9. Compare models on explicit criteria (architecture, input format, pretraining data, supported tasks, perturbation capability, batch correction, benchmarks, metrics, disease relevance).
10. Prefer simple, Obsidian-readable Markdown.
11. Keep everything plain Markdown.
12. No vector database (yet).
13. Keep the system simple and usable today.

---

## License / status

Research notes, maintained collaboratively by humans and an LLM agent. Treat all content as **secondary** notes — always confirm against the cited primary sources before relying on a claim.
