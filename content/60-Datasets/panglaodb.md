---
title: PanglaoDB
aliases: [PanglaoDB, Panglao DB, panglaodb]
type: dataset
modality: scRNA-seq
tags: [dataset, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# PanglaoDB

## Overview
PanglaoDB is a curated database of single-cell RNA-seq experiments together with a manually curated catalog of cell-type marker genes. It aggregates re-processed public scRNA-seq samples (largely from human and mouse) and is widely used as both a marker resource for cell-type annotation and a source of pretraining cells.

## Modality & content
- Assay: scRNA-seq.
- Species: human and mouse.
- Content: re-processed sample-level expression data plus a curated marker-gene/cell-type table.
- Scale: on the order of millions of cells across hundreds of samples (exact totals needs verification).

## Access
- Portal: panglaodb.se (web interface + downloadable processed matrices and marker tables).
- License: academic/non-commercial terms as stated on the site (needs verification).

## Used by
- [[scBERT]] — reported to use PanglaoDB scRNA-seq data for pretraining (needs verification of the exact subset/version).
- Marker tables are commonly used as references in [[cell type annotation benchmark]] evaluation (annotation by marker overlap).

## Notes & caveats
- Re-processing pipeline and inclusion criteria differ from the original studies; batch/platform heterogeneity is substantial.
- Marker lists are curated and incomplete; absence of a marker is not evidence of absence.
- Update cadence is irregular; cite the access date/version.

## Related
- [[CELLxGENE Census]], [[Human Cell Atlas]]
- [[cell type annotation benchmark]]
- [[scBERT]]

## Tags
#dataset #scfm #needs-verification
