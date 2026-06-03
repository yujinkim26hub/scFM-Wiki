---
title: single-cell foundation models for disease biology
aliases: [single-cell foundation models for disease biology, scFMs for disease biology, foundation models for disease biology]
type: topic
tags: [topic, scfm, disease, needs-verification]
status: stub
updated: 2026-06-03
---

# single-cell foundation models for disease biology

## Scope
How [[single-cell foundation models|scFMs]] are applied to disease-relevant single-cell data, and how reliable those applications currently are. This topic is cross-cutting: it spans annotation of diseased tissue, disease-state classification, and in-silico perturbation of disease genes. It is the parent for disease-domain pages such as [[single-cell foundation models for neurological disease]] and [[single-cell foundation models for microglia]].

The central tension: scFMs are pretrained almost entirely on healthy/reference atlases, yet most disease-biology interest is in *altered* cells and states. Whether learned representations transfer to disease contexts is largely an open empirical question.

## Key questions
- Do embeddings pretrained on (mostly healthy) reference data carry over to diseased tissue, where cell states are shifted or novel?
- Can scFMs classify disease vs control, or disease subtype, better than simpler supervised baselines? Under what protocol ([[zero-shot]], [[fine-tuning]])?
- When a model is used for [[in silico perturbation]] of a disease gene, what is actually predicted — an [[cell embedding|embedding]] shift, a classifier-score shift, or a [[transcriptome-level prediction|transcriptome-level]] change? (These are different claims; see [[perturbation prediction models]].)
- Is any disease application validated against experimental ground truth, or only shown to be internally consistent?

## Models involved
- [[Geneformer]] — in-silico perturbation framed as an [[cell embedding|embedding]] shift toward/away from a disease-vs-healthy state; rank-based gene tokenization. Output is an embedding/state-classifier signal, not a predicted transcriptome (needs verification of specifics per paper).
- [[scGPT]] — [[cell type annotation]] and disease-state classification via [[fine-tuning]]; can be fine-tuned for perturbation response.
- [[scFoundation]] — large-scale pretraining; used as an embedding source for downstream disease tasks.
- [[scBERT]], [[CellPLM]], [[scPRINT]], [[UCE]], [[GeneCompass]], [[scMamba]] — general scFMs that could supply embeddings for disease classification/annotation; disease-specific validation is sparse (needs verification).
- Perturbation-specific models [[GEARS]], [[CPA]], [[scGen]] are *not* pretrained scFMs but are relevant when the disease question is perturbation response; they predict at the [[transcriptome-level prediction|transcriptome level]].

## Key papers
To be ingested via the paper workflow (see AGENTS.md §3). No summaries exist yet. Candidate well-known references (all needs-verification until ingested):
- Theodoris et al., Geneformer (2023) — in-silico perturbation and disease-state shift, cardiomyopathy example (needs verification).
- Cui et al., scGPT (2024) — annotation/perturbation fine-tuning (needs verification).

## State of the evidence
- **Demonstrated:** scFM embeddings can be used to annotate and cluster cells from disease datasets; fine-tuned classifiers can separate disease vs control on specific datasets. These are real but modest, dataset-specific results.
- **Weakly supported / aspirational:** that scFMs identify *novel* disease mechanisms, or that in-silico perturbation of a disease gene reliably predicts the true experimental response. Most "disease insight" demonstrations are retrospective and not experimentally validated in the same paper.
- **Important caution:** an in-silico perturbation result expressed as an embedding/classifier shift is *not* a transcriptome-level prediction and should not be read as "the model predicts what happens to the cell." Keep [[zero-shot]], [[fine-tuning]], and supervised perturbation prediction separate.
- **Generalization gap:** pretraining corpora are dominated by healthy reference tissue; transfer to disease states is plausible but under-tested (needs verification). See [[benchmarking single-cell foundation models]] for independent results questioning scFM advantages.

## Open questions
- How much disease-specific signal survives in embeddings pretrained on healthy atlases?
- Are scFMs better than well-tuned simple baselines (e.g. logistic regression on HVGs, scVI) for disease classification?
- What experimental validation exists for any scFM-derived disease mechanism?
- Can disease-relevant rare/novel cell states be detected zero-shot, or only after fine-tuning on labeled disease data?

## Related
- Concepts: [[in silico perturbation]], [[cell type annotation]], [[zero-shot]], [[fine-tuning]], [[cell embedding]], [[transcriptome-level prediction]]
- Topics: [[single-cell foundation models for neurological disease]], [[single-cell foundation models for microglia]], [[perturbation prediction models]], [[benchmarking single-cell foundation models]]
- Benchmarks: [[cell type annotation benchmark]]

## Tags
#topic #scfm #disease #needs-verification
