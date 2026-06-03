---
title: Human Cell Atlas
aliases: [Human Cell Atlas, HCA, human cell atlas]
type: dataset
modality: scRNA-seq
tags: [dataset, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# Human Cell Atlas

## Overview
The Human Cell Atlas (HCA) is an international consortium effort to build comprehensive reference maps of all human cells as a basis for understanding health and disease. It coordinates many tissue- and organ-specific atlas projects and provides a Data Portal that hosts standardized single-cell datasets and reference atlases.

## Modality & content
- Assay: predominantly scRNA-seq and snRNA-seq; some multi-omic and spatial data within member projects.
- Species: human.
- Coverage: many organs/tissues across developmental stages and donors.
- Scale: tens of millions of cells aggregated across constituent projects (exact totals vary by release — needs verification).

## Access
- Portal: HCA Data Portal (data.humancellatlas.org); many datasets also surfaced via CELLxGENE.
- License: per-project; consult individual dataset terms (needs verification).

## Used by
- Constituent atlases (e.g. [[Tabula Sapiens]]) are frequently used as pretraining and/or evaluation data by scFMs; per-model provenance needs verification (pretraining vs evaluation).
- Reference atlases are common targets for [[cell type annotation benchmark]] and [[cell embedding benchmark]].

## Notes & caveats
- HCA is an umbrella consortium, not a single fixed dataset; "used HCA" claims should specify the constituent project and version.
- Strong donor/lab/protocol batch structure relevant to [[batch correction benchmark]].

## Related
- [[Tabula Sapiens]], [[CELLxGENE Census]]
- [[cell type annotation benchmark]], [[biological conservation benchmark]]

## Tags
#dataset #scfm #needs-verification
