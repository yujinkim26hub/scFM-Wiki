---
title: cell embedding benchmark
aliases: [cell embedding benchmark, cell-embedding benchmark, cell embedding quality, embedding benchmark]
type: benchmark
tags: [benchmark, scfm]
status: stub
updated: 2026-06-03
---

# cell embedding benchmark

## Task definition
Evaluate the quality of a model's per-cell embedding (latent representation) by how well unsupervised structure in the embedding aligns with known biology — typically whether clustering of the embedding recovers ground-truth cell-type labels.

## Common datasets
- Annotated atlases with reliable labels: [[Tabula Sapiens]], [[Human Cell Atlas]] constituents.
- [[CELLxGENE Census]] subsets.
- Standard scIB collections (needs verification of exact sets).

## Metrics
- **Clustering vs labels**: ARI (Adjusted Rand Index), NMI (Normalized Mutual Information) between clusters (e.g. Leiden) and ground-truth labels.
- **Separation**: cell-type ASW (silhouette), graph connectivity.
- Blind spots: ARI/NMI depend on clustering resolution and label granularity; ASW assumes roughly convex, comparably-scaled clusters. All depend on label quality. None directly measure batch mixing (see [[batch correction benchmark]]).

## How models are evaluated here
- **Zero-shot**: frozen scFM embeddings clustered and scored — the primary scFM use case here.
- **Fine-tuned**: embeddings from a fine-tuned model.
- Report which protocol; numbers are not interchangeable.

## Models evaluated
- [[scGPT]], [[Geneformer]], [[scFoundation]], [[UCE]], [[CellPLM]] — reported embedding/clustering results; per-model dataset and protocol needs verification.
- Baselines: HVG + PCA, scVI embeddings — often strong comparators (see [[zero-shot benchmark]]).

## Caveats
- Resolution dependence: ARI/NMI vary with the number of clusters chosen.
- Label leakage from pretraining overlap inflates apparent quality.
- High cell-type separation alone is insufficient if batches are unmixed; pair with bio + batch metrics.
- Cross-paper comparability limited by differing datasets, clustering, and label sets.

## Related
- [[cell type annotation benchmark]], [[batch correction benchmark]], [[biological conservation benchmark]], [[zero-shot benchmark]]
- [[Tabula Sapiens]], [[CELLxGENE Census]]

## Tags
#benchmark #scfm
