---
title: CROP-seq datasets
aliases: [CROP-seq datasets, CROP-seq, crop-seq, CROP-seq data]
type: dataset
modality: perturbation
tags: [dataset, scfm, perturbation, needs-verification]
status: stub
updated: 2026-06-03
---

# CROP-seq datasets

## Overview
CROP-seq (CRISPR droplet sequencing) is a pooled CRISPR screening method with single-cell RNA-seq readout in which the guide RNA is captured directly in the polyadenylated transcript, simplifying guide-to-cell assignment in droplet platforms. It is closely related to [[Perturb-seq datasets]]; the main distinction is the guide-capture/vector design.

## Modality & content
- Assay: pooled CRISPR (often CRISPRi) + droplet scRNA-seq; guide captured as an expressed transcript.
- Species: human/mouse cell lines and some primary systems (per study; needs verification).
- Content: cell-by-gene expression matrices with per-cell guide assignments.

## Access
- Via GEO accessions in the originating papers (e.g. Datlinger et al. 2017 introduced CROP-seq; accession needs verification).
- License: per-study.

## Used by
- Used as perturbation training/evaluation data by perturbation-response models alongside Perturb-seq; exact usage per model ([[GEARS]], [[scGPT]] perturbation) needs verification.

## Notes & caveats
- Guide-capture chemistry differs from array-based Perturb-seq, which can change assignment confidence and dropout characteristics.
- Same cell-line generalization and label-noise caveats as [[Perturb-seq datasets]].

## Related
- [[Perturb-seq datasets]]
- [[perturbation prediction benchmark]]
- [[GEARS]], [[scGPT]]

## Tags
#dataset #scfm #perturbation #needs-verification
