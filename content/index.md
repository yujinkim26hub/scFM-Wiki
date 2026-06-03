---
title: scFM-Wiki
aliases: [home, scFM-Wiki]
type: note
tags: [home, scfm]
status: draft
updated: 2026-06-03
---

# scFM-Wiki

A living, LLM-maintained wiki on **single-cell foundation models (scFMs)**, **virtual cell models**, and their biomedical applications — with an emphasis on careful, non-overclaiming descriptions of what each model actually consumes, produces, and has been validated to do.

> **How to read this wiki.** Capability claims are deliberately conservative. Watch for the distinction between *zero-shot* use of frozen embeddings, *fine-tuning*, and *supervised perturbation prediction*; and between an *embedding shift*, a *classifier-score shift*, and a *true transcriptome-level prediction*. Anything marked `unclear` or `needs verification` has not been confirmed against a primary source.

## Start here

- 🗂️ **[[catalog|Catalog]]** — master index of every page.
- 🪵 **[[log|Log]]** — chronological ingestion / edit log.
- 🧩 [[single-cell foundation model]] — the central concept.
- ⚖️ [[model comparison overview]] — how the tracked models line up across shared criteria.

## Models

General scFMs: [[Geneformer]] · [[scGPT]] · [[scFoundation]] · [[scBERT]] · [[scMamba]] · [[CellPLM]] · [[scPRINT]] · [[UCE]] · [[GeneCompass]]

Perturbation-specific models: [[GEARS]] · [[CPA]] · [[scGen]]

→ all in `20-Models/`.

## Concepts

[[gene embedding]] · [[cell embedding]] · [[gene relationship]] · [[gene regulatory network]] · [[cell state]] · [[cell state shift]] · [[in silico perturbation]] · [[perturbation prediction]] · [[zero-shot prediction]] · [[fine-tuning]] · [[transfer learning]] · [[batch correction]] · [[data integration]] · [[tokenization strategy]] · [[expression value encoding]] · [[rank-based encoding]] · [[condition token]] · [[model interpretability]] · [[virtual cell model]]

## Topics

[[single-cell foundation models for disease biology]] · [[single-cell foundation models for neurological disease]] · [[single-cell foundation models for microglia]] · [[perturbation prediction models]] · [[batch correction and atlas integration]] · [[cell type annotation using foundation models]] · [[benchmarking single-cell foundation models]] · [[virtual cell models and biological simulation]]

## Datasets & benchmarks

Datasets: [[CELLxGENE Census]] · [[PanglaoDB]] · [[Human Cell Atlas]] · [[Tabula Sapiens]] · [[Perturb-seq datasets]] · [[CROP-seq datasets]] · [[single-cell brain atlas datasets]] · [[microglia single-cell datasets]]

Benchmarks: [[cell type annotation benchmark]] · [[batch correction benchmark]] · [[perturbation prediction benchmark]] · [[gene relationship benchmark]] · [[cell embedding benchmark]] · [[zero-shot benchmark]] · [[disease classification benchmark]] · [[biological conservation benchmark]]

## Questions this wiki is built to answer

- What are the major single-cell foundation models, and how do they differ?
- Which models support zero-shot analysis vs require fine-tuning?
- Which models can perform in silico perturbation, and which predict *transcriptome-level* responses vs only embedding/cell-state shifts?
- Which models require perturbation datasets?
- Which support batch correction / data integration, and which are good for cell type annotation?
- What input format and gene/expression encoding does each model use?
- What pretraining datasets and benchmark tasks were used?
- How reliable are these models for disease biology — including microglia, Alzheimer's, neurodegeneration, neuropsychiatric disease?
- What are the limitations of current scFMs and the open questions in virtual cell modeling?

## Add a paper

Give the agent: First author · Title · Year · Venue · Section · Model (if any) · Main task. It verifies identity, writes a 24-field summary in `10-Summaries/`, and propagates updates. Unverifiable requests go to [[unresolved-paper-requests]]. See [[AGENTS]] for the full workflow.
