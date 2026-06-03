---
title: batch correction
aliases: [batch correction, batch effect removal, batch effect]
type: concept
tags: [concept, scfm, batch-correction]
status: stub
updated: 2026-06-03
---

# batch correction

## Definition
Batch correction removes technical variation introduced by differences in sample preparation, sequencing run, platform, lab, or time ("batch effects"), so that cells cluster by biology rather than by technical origin. A **batch effect** is the unwanted technical variation itself.

## Why it matters for scFMs
[[single-cell foundation model|scFMs]] are frequently evaluated on their ability to produce [[cell embedding|embeddings]] that mix batches while preserving cell identity — a core part of [[data integration]]. It is a standard benchmark axis (often via scIB metrics).

## How it works / key distinctions
- Metrics for **batch mixing**: kBET, iLISI (batch LISI), graph connectivity.
- Metrics for **biological conservation**: ARI, NMI, cLISI, isolated-label scores. Composite scores (e.g. scIB) trade these off.
- Correction can happen in raw/normalized space (e.g. Harmony, scVI, Combat) or implicitly inside an scFM embedding.

## Common pitfalls / what it is not
- **Tradeoff with biological signal:** aggressive batch removal can erase real biological variation (over-integration). High batch-mixing scores alone are not success; bio-conservation must hold too.
- Removing a batch effect is not the same as removing all confounding; biological and technical variation can be entangled.
- Good batch mixing does not imply correct cell-type separation.

## Models / methods that use it
- scFMs benchmarked on it: [[scGPT]], [[scFoundation]], [[Geneformer]], [[UCE]], [[CellPLM]], [[scMamba]] (results vary; needs verification). Classical baselines: Harmony, scVI, Combat.

## Related concepts
[[data integration]], [[cell embedding]], [[zero-shot prediction]]

## Tags
#concept #scfm #batch-correction #needs-verification
