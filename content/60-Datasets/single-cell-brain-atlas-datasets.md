---
title: single-cell brain atlas datasets
aliases: [single-cell brain atlas datasets, single-cell brain atlas, brain atlas datasets, brain single-cell atlas]
type: dataset
modality: snRNA-seq
tags: [dataset, scfm, neuro, needs-verification]
status: stub
updated: 2026-06-03
---

# single-cell brain atlas datasets

## Overview
A collection of large human and mouse brain single-nucleus / single-cell RNA-seq reference atlases that map neuronal and non-neuronal cell types and states across brain regions. These atlases are the reference substrate for neuro-focused scFM applications, including cell-type annotation and disease-state analysis.

## Modality & content
- Assay: predominantly snRNA-seq (frozen brain tissue favors nuclei); some scRNA-seq and multi-omic.
- Species: human and mouse.
- Example sources (needs verification of exact versions/counts):
  - Allen Brain Atlas / Allen Institute human and mouse brain taxonomies.
  - BICCN / BRAIN Initiative Cell Census Network whole-brain atlases.
  - Various cortical and region-specific atlases.
- Scale: millions of nuclei across regions.

## Access
- Allen Brain Map (portal.brain-map.org), NeMO Archive (BICCN), and associated GEO accessions. Specific URLs/accessions needs verification.
- License: per-project (often open).

## Used by
- Used as evaluation/reference data for neuro-oriented scFM analyses (cell-type annotation, embedding); specific model usage and whether pretraining vs evaluation needs verification.

## Notes & caveats
- Nucleus-based assays under-sample cytoplasmic and activity-dependent transcripts vs whole-cell scRNA-seq.
- Strong region/donor/protocol batch structure (relevant to [[batch correction benchmark]]).
- Cell-type taxonomies differ across consortia; label harmonization is nontrivial.

## Related
- [[microglia single-cell datasets]]
- [[Human Cell Atlas]]
- [[cell type annotation benchmark]], [[disease classification benchmark]]

## Tags
#dataset #scfm #neuro #needs-verification
