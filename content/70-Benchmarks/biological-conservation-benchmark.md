---
title: biological conservation benchmark
aliases: [biological conservation benchmark, biological conservation, bio-conservation benchmark, bio conservation]
type: benchmark
tags: [benchmark, scfm, batch-correction]
status: stub
updated: 2026-06-03
---

# biological conservation benchmark

## Task definition
Measure whether an integrated/learned representation **preserves biological signal** — cell-type and cell-state structure — rather than washing it out during batch correction. It is the bio-conservation half of the scIB framework, the counterweight to batch-removal metrics in the [[batch correction benchmark]].

## Common datasets
- Annotated, multi-batch atlases: [[Human Cell Atlas]], [[Tabula Sapiens]], [[CELLxGENE Census]] subsets.
- scIB benchmark collections (Immune, Pancreas, Lung; needs verification).

## Metrics (scIB bio-conservation group)
- Cell-type ASW (silhouette by label).
- Isolated-label scores (ASW and F1) — how well rare/isolated labels stay separable.
- NMI and ARI of clustering vs labels.
- cLISI (cell-type LISI) — local label purity.
- kBET within label, graph-based label conservation.
- Blind spots: all are label-dependent (noisy labels cap scores); isolated-label metrics are sensitive to how "isolated" is defined; high bio-conservation with poor batch mixing means the model simply did not integrate.

## How models are evaluated here
- **Zero-shot**: frozen scFM embeddings scored with scIB bio-conservation metrics (most common scFM claim).
- **Fine-tuned**: embeddings after integration-oriented fine-tuning.
- Report which; pair with batch-removal metrics to see the full tradeoff.

## Models evaluated
- [[scGPT]], [[Geneformer]], [[scFoundation]], [[UCE]], [[CellPLM]] — reported scIB bio-conservation results; per-model protocol/dataset needs verification.
- Baselines: scVI, scANVI, Harmony, and unintegrated HVG + PCA (which trivially maxes bio-conservation but fails batch removal).

## Caveats
- Reported in isolation, bio-conservation is misleading: doing nothing (no integration) scores high. It is only meaningful jointly with batch-removal metrics.
- Aggregate scIB weighting between bio and batch groups changes rankings; report components.
- Label quality and granularity drive the numbers.
- Cross-paper comparability limited by dataset versions and metric choices.

## Related
- [[batch correction benchmark]], [[cell embedding benchmark]], [[zero-shot benchmark]]
- [[Human Cell Atlas]], [[Tabula Sapiens]], [[CELLxGENE Census]]

## Tags
#benchmark #scfm #batch-correction
