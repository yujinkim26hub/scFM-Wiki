---
title: data integration
aliases: [data integration, atlas mapping]
type: concept
tags: [concept, scfm, batch-correction]
status: stub
updated: 2026-06-03
---

# data integration

## Definition
Data integration combines multiple single-cell datasets (across batches, donors, platforms, tissues, or modalities) into a shared representation so that comparable cells align regardless of source. **Atlas mapping** (query-to-reference) is a special case: embedding new "query" cells into an existing reference [[cell embedding|embedding]] space.

## Why it matters for scFMs
Integration is a primary claimed strength of [[single-cell foundation model|scFMs]]: their [[cell embedding|cell embeddings]] are meant to provide a universal space into which new datasets map. It is closely tied to [[batch correction]] and is a major benchmark axis.

## How it works / key distinctions
- Evaluated with **scIB** metrics: a weighted combination of batch-removal scores (iLISI, kBET, graph connectivity) and bio-conservation scores (ARI, NMI, cLISI, isolated labels).
- **Atlas/query-to-reference mapping** reuses a fixed reference; the query is projected, optionally with light fine-tuning.
- Integration may be [[zero-shot prediction|zero-shot]] (frozen embeddings) or after [[fine-tuning]] — state which.

## Common pitfalls / what it is not
- Integration is not free of the [[batch correction]] tradeoff: over-mixing destroys biology.
- A shared space does not guarantee biologically correct alignment; verify with held-out labels.
- scFM integration does not always beat scVI/Harmony, especially zero-shot (needs verification of specifics).

## Models / methods that use it
- [[scGPT]], [[scFoundation]], [[Geneformer]], [[UCE]], [[CellPLM]], [[scMamba]], [[scPRINT]] evaluated on integration/atlas mapping (results vary; needs verification).

## Related concepts
[[batch correction]], [[cell embedding]], [[zero-shot prediction]], [[transfer learning]]

## Tags
#concept #scfm #batch-correction #needs-verification
