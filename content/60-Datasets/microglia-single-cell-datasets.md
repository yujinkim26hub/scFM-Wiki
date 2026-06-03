---
title: microglia single-cell datasets
aliases: [microglia single-cell datasets, microglia single-cell data, microglia scRNA-seq, microglia snRNA-seq]
type: dataset
modality: snRNA-seq
tags: [dataset, scfm, neuro, needs-verification]
status: stub
updated: 2026-06-03
---

# microglia single-cell datasets

## Overview
Microglia-focused single-cell and single-nucleus RNA-seq datasets profile the brain's resident immune cells and their transcriptional states, including homeostatic microglia and disease-associated states. These datasets underpin study of microglial heterogeneity in neurodegeneration, especially Alzheimer's disease (AD).

## Modality & content
- Assay: snRNA-seq and scRNA-seq; some sorted-microglia and spatial studies.
- Species: human and mouse.
- States of interest (needs verification of definitions across studies):
  - Homeostatic microglia.
  - Disease-associated microglia (DAM) / activated states.
  - AD- and aging-associated microglial subpopulations.
- Scale: ranges from thousands to hundreds of thousands of cells/nuclei per study.

## Access
- Distributed via study-specific GEO/Synapse accessions (e.g. AD cohort resources); specific accessions and counts needs verification.
- License: per-study; some require controlled access (human brain cohorts).

## Used by
- Used mainly as evaluation/application data for disease-state classification and cell-state analysis; specific scFM usage and protocol (zero-shot vs fine-tuned) needs verification.

## Notes & caveats
- Microglial activation states are sensitive to dissociation/ex vivo artifacts; snRNA-seq mitigates but under-samples some transcripts.
- DAM nomenclature is largely mouse-derived; human correspondence is debated (needs verification).
- Small-cohort, case/control designs risk confounding disease signal with batch — relevant to [[disease classification benchmark]].

## Related
- [[single-cell brain atlas datasets]]
- [[disease classification benchmark]], [[cell type annotation benchmark]]

## Tags
#dataset #scfm #neuro #needs-verification
