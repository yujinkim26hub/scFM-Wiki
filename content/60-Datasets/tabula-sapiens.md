---
title: Tabula Sapiens
aliases: [Tabula Sapiens, tabula sapiens, Tabula Sapiens atlas]
type: dataset
modality: scRNA-seq
tags: [dataset, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# Tabula Sapiens

## Overview
Tabula Sapiens is a multi-organ single-cell reference atlas of the human body, generated from multiple organs of a small number of human donors and processed with a harmonized pipeline. It is a member project of the [[Human Cell Atlas]] and provides consistently annotated cell-type labels across tissues, making it a convenient cross-tissue reference.

## Modality & content
- Assay: scRNA-seq (droplet and plate-based, e.g. 10x and Smart-seq2).
- Species: human.
- Coverage: ~25 organs/tissues (needs verification) from a handful of donors.
- Scale: on the order of several hundred thousand cells (~500k, needs verification).

## Access
- Portal: tabula-sapiens-portal.ds.czbiohub.org; also distributed via CELLxGENE and figshare.
- License: open data terms (CC; specific variant needs verification).

## Used by
- Used by various scFMs as a cross-tissue evaluation set for [[cell type annotation benchmark]] and [[cell embedding benchmark]]; some may include it in pretraining corpora (pretraining vs evaluation per model needs verification).

## Notes & caveats
- Few donors → limited inter-individual variation; not representative of population diversity.
- Multiple assay platforms within the atlas introduce technical batch effects (relevant to [[batch correction benchmark]]).

## Related
- [[Human Cell Atlas]], [[CELLxGENE Census]]
- [[cell type annotation benchmark]], [[cell embedding benchmark]]

## Tags
#dataset #scfm #needs-verification
