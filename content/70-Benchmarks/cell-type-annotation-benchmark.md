---
title: cell type annotation benchmark
aliases: [cell type annotation benchmark, cell-type annotation benchmark, cell type annotation, cell-type annotation]
type: benchmark
tags: [benchmark, scfm]
status: stub
updated: 2026-06-03
---

# cell type annotation benchmark

## Task definition
Given a cell's expression profile, predict its cell-type label. Evaluated as a supervised classification task against ground-truth (often author- or atlas-provided) labels, typically with train/test splits across cells, donors, or datasets.

## Common datasets
- [[Tabula Sapiens]], [[Human Cell Atlas]] constituent atlases.
- [[PanglaoDB]] marker tables (for marker-based annotation references).
- Standard scFM annotation sets (e.g. Multiple Sclerosis, hPancreas, Myeloid; needs verification of exact splits per paper).

## Metrics
- Accuracy — rewards majority classes; can hide poor performance on rare types.
- Macro-F1 — averages per-class F1, exposing rare-class failures; preferred for imbalanced data.
- Per-class precision/recall and confusion matrices give finer detail.
- Blind spot: metrics depend entirely on label quality; noisy/ontology-inconsistent ground truth caps the achievable score and can penalize biologically reasonable predictions.

## How models are evaluated here
- **Fine-tuned**: pretrained scFM with a classification head trained on labeled cells (most reported scFM annotation results). Distinct from zero-shot.
- **Zero-shot**: frozen embeddings + a simple classifier (kNN/logistic regression), or nearest-reference matching, with no scFM weight updates.
- The two protocols are not comparable and must be reported separately (AGENTS §0.2).

## Models evaluated
- [[scGPT]] — reported fine-tuned annotation results (source/summary needed).
- [[Geneformer]] — reported fine-tuned cell-classification results.
- [[scBERT]] — introduced for cell-type annotation via fine-tuning.
- [[CellPLM]], [[UCE]], [[scFoundation]] — reported on annotation tasks; protocol (zero-shot vs fine-tuned) per paper needs verification.

## Caveats
- Label leakage: if pretraining cells overlap test cells, scores are inflated.
- Cross-dataset generalization (annotate an unseen dataset) is much harder than within-dataset splits; many headline numbers are within-dataset.
- Batch confounding: a model may exploit batch signal correlated with cell type.
- Comparability across papers is poor due to differing datasets, splits, and label ontologies.

## Related
- [[cell embedding benchmark]], [[zero-shot benchmark]]
- [[Tabula Sapiens]], [[PanglaoDB]]

## Tags
#benchmark #scfm
