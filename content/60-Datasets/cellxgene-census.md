---
title: CELLxGENE Census
aliases: [CELLxGENE Census, CELLxGENE, cellxgene census, CZ CELLxGENE Census]
type: dataset
modality: scRNA-seq
tags: [dataset, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# CELLxGENE Census

## Overview
CELLxGENE Census is the Chan Zuckerberg Initiative (CZI) standardized aggregation of publicly available single-cell data, exposed through the CELLxGENE Discover platform. It harmonizes many independent studies into a single queryable corpus with consistent gene identifiers (Ensembl), cell metadata, and ontology-mapped cell-type labels. It is released as versioned snapshots (LTS and weekly builds).

## Modality & content
- Assay: primarily scRNA-seq (also some snRNA-seq); standardized to a common gene-by-cell matrix.
- Species: human and mouse.
- Scale: tens of millions of cells aggregated across hundreds of datasets (exact counts grow per release — needs verification for any specific number).
- Metadata: tissue, disease, sex, assay, donor, cell-type (CL ontology) labels.

## Access
- Portal: CELLxGENE Discover (cellxgene.cziscience.com) and the `cellxgene-census` Python/R API.
- License: per-dataset licensing aggregated by CZI; check individual dataset terms (needs verification).

## Used by
- [[scGPT]] — reported to use large public single-cell collections for pretraining; whether the specific CELLxGENE Census snapshot was the pretraining source needs verification.
- Various scFMs draw pretraining cells from CELLxGENE-hosted data; specific provenance per model needs verification (pretraining vs evaluation).

## Notes & caveats
- Snapshots are versioned; reproducibility requires citing the exact Census version. Numbers above are approximate.
- Aggregation introduces strong study/batch structure; relevant to [[batch correction benchmark]] and [[biological conservation benchmark]].
- Cell-type labels are ontology-mapped but originate from heterogeneous original studies (label noise).

## Related
- [[Human Cell Atlas]], [[Tabula Sapiens]]
- [[batch correction benchmark]], [[cell type annotation benchmark]]
- [[scGPT]]

## Tags
#dataset #scfm #needs-verification
