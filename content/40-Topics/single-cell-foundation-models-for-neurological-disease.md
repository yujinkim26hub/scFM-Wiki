---
title: single-cell foundation models for neurological disease
aliases: [single-cell foundation models for neurological disease, scFMs for neurological disease, foundation models for neurological disease]
type: topic
tags: [topic, scfm, disease, neuro, needs-verification]
status: stub
updated: 2026-06-03
---

# single-cell foundation models for neurological disease

## Scope
Application of [[single-cell foundation models|scFMs]] to neurodegenerative, neurodevelopmental, and neuropsychiatric disease — e.g. Alzheimer's disease (AD), Parkinson's disease (PD), ALS, frontotemporal dementia, autism-spectrum and schizophrenia-associated transcriptomic studies. A specialization of [[single-cell foundation models for disease biology]].

The brain poses specific challenges for scFMs: high cell-type diversity, non-neuronal populations ([[single-cell foundation models for microglia|microglia]], astrocytes, oligodendrocytes) central to disease, post-mortem/snRNA-seq data quality, and disease states (e.g. reactive glia) that are under-represented in healthy reference atlases.

## Key questions
- Do scFM embeddings trained on broad reference atlases capture brain-cell heterogeneity well enough for disease work?
- Can scFMs annotate diseased brain tissue (e.g. AD prefrontal cortex) reliably, including rare disease-associated states?
- Does in-silico perturbation of risk genes (APOE, TREM2, SNCA, MAPT) yield anything beyond an [[cell embedding|embedding]] shift, and is it validated?
- How do scFMs compare to brain-specialized or simply well-tuned baseline pipelines on neuro datasets?

## Models involved
- [[Geneformer]], [[scGPT]] — most commonly applied to disease annotation and in-silico perturbation; neuro-specific validation is limited (needs verification).
- [[scFoundation]], [[CellPLM]], [[UCE]], [[scPRINT]], [[GeneCompass]], [[scBERT]], [[scMamba]] — general scFMs usable on brain data as embedding/annotation tools; few have dedicated neurological-disease evaluations (needs verification).
- For perturbation of risk genes as a *response prediction* task, see [[perturbation prediction models]] ([[GEARS]], [[CPA]], [[scGen]]).

## Key papers
To be ingested via the paper workflow (see AGENTS.md §3). No summaries exist yet. Most scFM papers use one or two neuro datasets as examples rather than performing systematic neurological-disease validation (needs verification).

## State of the evidence
- **Demonstrated:** scFMs can embed and annotate brain single-cell/single-nucleus datasets; some papers include AD/PD datasets as illustrative cases.
- **Limited:** there is little systematic, externally validated evidence that scFMs outperform established brain-data pipelines on neurological-disease tasks. Disease-mechanism claims are largely retrospective.
- **Aspirational:** that in-silico perturbation of neurodegeneration risk genes predicts true cellular responses. Treat such results as embedding/classifier signals unless transcriptome-level prediction is explicitly validated.
- **Honest summary:** this is an emerging, under-validated application area. Most evidence is anecdotal/illustrative, not benchmark-grade (needs verification).

## Open questions
- Does pretraining on healthy reference tissue under-represent reactive/disease glial states critical to neurodegeneration?
- Can scFMs distinguish disease stage or genotype (e.g. APOE status) from transcriptome alone?
- What independent neuro benchmark, if any, exists for scFMs?

## Related
- Datasets: [[single-cell brain atlas datasets]], [[microglia single-cell datasets]]
- Topics: [[single-cell foundation models for disease biology]], [[single-cell foundation models for microglia]], [[perturbation prediction models]], [[benchmarking single-cell foundation models]]
- Concepts: [[cell type annotation]], [[in silico perturbation]], [[zero-shot]], [[fine-tuning]]

## Tags
#topic #scfm #disease #neuro #needs-verification
