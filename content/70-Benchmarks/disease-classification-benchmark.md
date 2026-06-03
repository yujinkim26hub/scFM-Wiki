---
title: disease classification benchmark
aliases: [disease classification benchmark, disease-classification benchmark, disease classification, disease state classification]
type: benchmark
tags: [benchmark, scfm, disease]
status: stub
updated: 2026-06-03
---

# disease classification benchmark

## Task definition
Classify cells, samples, or donors by disease status — disease vs control, or among disease states/subtypes — from single-cell expression. May be posed at the cell level (predict a cell's condition label) or at the sample/donor level (aggregate cells to predict a phenotype).

## Common datasets
- Disease cohort sc/snRNA-seq, e.g. [[microglia single-cell datasets]] (AD), [[single-cell brain atlas datasets]] (neurodegeneration).
- Other case/control single-cell studies (immune, cancer; needs verification of specific sets).

## Metrics
- AUROC, accuracy, macro-F1 (for multi-state), AUPRC for imbalanced positives.
- Sample/donor-level evaluation with grouped cross-validation when predicting phenotype.
- Blind spots: cell-level accuracy can be inflated when many cells come from few donors (pseudoreplication); AUROC at the sample level on tiny cohorts is high-variance and easily over-fit.

## How models are evaluated here
- **Fine-tuned**: scFM + classification head trained on labeled cells/samples (common for disease tasks).
- **Zero-shot**: frozen embeddings + simple classifier.
- Report which; also report whether evaluation is grouped by donor to avoid leakage.

## Models evaluated
- [[scGPT]], [[Geneformer]], [[scBERT]] — reported on disease/condition classification settings; per-paper protocol and dataset needs verification.
- Compare against simple baselines (pseudobulk + logistic regression), which are strong for sample-level phenotypes.

## Caveats
- **Small-cohort caution**: with few donors, the model can learn donor/batch identity rather than disease biology; donor-grouped splits are essential.
- Batch confound: disease and control samples processed in different batches make technical signal look like disease signal.
- Cell-level vs donor-level claims are different; a high cell-level AUROC does not imply donor-level diagnostic value.
- Controlled-access cohorts and differing label definitions limit cross-paper comparability.

## Related
- [[cell type annotation benchmark]], [[biological conservation benchmark]]
- [[microglia single-cell datasets]], [[single-cell brain atlas datasets]]

## Tags
#benchmark #scfm #disease
