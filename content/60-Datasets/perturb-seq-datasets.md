---
title: Perturb-seq datasets
aliases: [Perturb-seq datasets, Perturb-seq, perturb-seq, Perturb-seq data, Perturb-seq screens]
type: dataset
modality: perturbation
tags: [dataset, scfm, perturbation, needs-verification]
status: stub
updated: 2026-06-03
---

# Perturb-seq datasets

## Overview
Perturb-seq refers to pooled CRISPR screening combined with single-cell RNA-seq readout, in which each cell receives one (or more) guide RNAs and its full transcriptome is measured. The guide identity is recovered per cell, linking genetic perturbations to single-cell expression phenotypes. Several published Perturb-seq screens have become standard datasets for training and evaluating perturbation-response models.

## Modality & content
- Assay: pooled CRISPR (CRISPRi/CRISPRa/KO) + scRNA-seq; perturbation labels per cell.
- Common datasets (needs verification of exact composition):
  - Norman et al. 2019 — single and combinatorial (pairwise) CRISPRa perturbations in K562.
  - Replogle et al. 2022 — genome-scale CRISPRi Perturb-seq in K562/RPE1.
  - Adamson et al. 2016 — UPR-focused Perturb-seq.
  - Dixit et al. 2016 — original Perturb-seq.
- Species: human cell lines (predominantly).

## Access
- Typically via GEO accessions cited in each paper; some redistributed in processed form (e.g. via scPerturb). Specific accessions needs verification.
- License: per-study.

## Used by
- [[GEARS]] — uses Perturb-seq screens (e.g. Norman) for training and evaluation of perturbation-response prediction.
- [[scGPT]] — perturbation fine-tuning/evaluation uses Perturb-seq data (e.g. Norman, Adamson; needs verification of exact split).
- [[CPA]], [[scGen]] — perturbation-response models trained/evaluated on such data.
- See also [[CROP-seq datasets]] for a related screening modality.

## Notes & caveats
- Mostly immortalized cell lines; generalization to primary cells/tissues is uncertain.
- Guide assignment noise, variable knockdown efficiency, and MOI affect labels.
- Train/test splits matter: holding out unseen perturbations vs unseen combinations tests different generalization — see [[perturbation prediction benchmark]].
- True transcriptome-level prediction (delta expression) is distinct from embedding-shift outputs.

## Related
- [[CROP-seq datasets]]
- [[perturbation prediction benchmark]]
- [[GEARS]], [[CPA]], [[scGen]], [[scGPT]]

## Tags
#dataset #scfm #perturbation #needs-verification
