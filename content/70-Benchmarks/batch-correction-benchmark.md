---
title: batch correction benchmark
aliases: [batch correction benchmark, batch-correction benchmark, batch correction, data integration benchmark]
type: benchmark
tags: [benchmark, scfm, batch-correction]
status: stub
updated: 2026-06-03
---

# batch correction benchmark

## Task definition
Given cells from multiple batches (donors, labs, platforms, studies), produce an integrated representation in which technical batch differences are removed while biological structure (cell types/states) is preserved. Operationalized largely through the scIB evaluation framework.

## Common datasets
- Multi-batch integration sets: [[Human Cell Atlas]] / [[Tabula Sapiens]] multi-donor or multi-platform data.
- [[CELLxGENE Census]] cross-study aggregations (strong batch structure).
- scIB benchmark collections (Immune, Pancreas, Lung; needs verification of exact versions).

## Metrics
- **Batch removal**: kBET, iLISI (integration LISI), batch-ASW, graph connectivity, PCR-batch.
- **Bio-conservation** (see [[biological conservation benchmark]]): cell-type ASW, iso-label F1, NMI/ARI vs labels, cLISI.
- scIB reports a weighted aggregate of both groups.
- Blind spot / tradeoff: aggressive batch mixing can erase real biology; a high batch-removal score with low bio-conservation is over-correction. The single aggregate score hides this tradeoff and is sensitive to the weighting choice.

## How models are evaluated here
- **Zero-shot**: scFM frozen embeddings fed directly to scIB metrics (most common scFM integration claim).
- **Fine-tuned**: scFM fine-tuned with a batch-aware objective before metric computation.
- Report which; they are not comparable.

## Models evaluated
- [[scGPT]], [[Geneformer]], [[scFoundation]], [[UCE]], [[CellPLM]] — reported scIB integration results; per-model protocol and dataset needs verification.
- Classical baselines (Harmony, scVI, scANVI, BBKNN) are the relevant comparators and are often competitive.

## Caveats
- "Batch" definition varies (donor vs platform vs study); difficulty differs accordingly.
- Metric gaming: tuning toward batch-removal metrics can hurt downstream biology.
- Simple baselines (e.g. HVG + PCA + Harmony) are sometimes competitive with scFMs (needs verification) — see [[zero-shot benchmark]].
- Cross-paper comparability is limited by differing dataset versions and metric weightings.

## Related
- [[biological conservation benchmark]], [[cell embedding benchmark]], [[zero-shot benchmark]]
- [[CELLxGENE Census]], [[Human Cell Atlas]]

## Tags
#benchmark #scfm #batch-correction
