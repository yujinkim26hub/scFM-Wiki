---
title: cell state shift
aliases: [cell state shift, cell-state shift, cell state transition]
type: concept
tags: [concept, scfm, perturbation]
status: stub
updated: 2026-06-03
---

# cell state shift

## Definition
A cell-state shift is a movement of a cell's representation in [[cell embedding|embedding]] (or [[cell state]]) space, typically observed after a (real or simulated) perturbation. It is measured as a change in position/direction in the model's latent space.

## Why it matters for scFMs
[[in-silico perturbation]] in models like [[Geneformer]] works by altering input (e.g. deleting a gene token) and measuring how far and in what direction the [[cell embedding]] moves. This shift is used to rank genes by predicted impact or to suggest a cell would move toward another state.

## How it works / key distinctions
**This is the most important distinction on this page.** A cell-state shift is **NOT** the same as predicting the post-perturbation transcriptome:

| Quantity | What it is | Example model |
|---|---|---|
| Cell-state / embedding shift | Δ in latent space | [[Geneformer]] in-silico perturbation |
| Classifier-score shift | Δ in a trained classifier's output (e.g. disease prob.) | classifier-head readouts |
| Transcriptome-level prediction | Predicted expression vector for each gene post-perturbation | [[GEARS]], [[CPA]], [[scGen]], [[scGPT]] fine-tuned |

An embedding shift tells you the representation changed and in which direction; it does **not** give you per-gene expression values, and it is not validated against measured responses unless explicitly benchmarked.

## Common pitfalls / what it is not
- Do not report an embedding shift as a "perturbation prediction" of gene expression (AGENTS.md §0.3).
- Direction/magnitude in latent space is model- and training-dependent; it is not a direct biological readout.
- A shift "toward healthy state" is an interpretation of geometry, not a measured outcome.

## Models / methods that use it
- [[Geneformer]] (embedding-shift in-silico perturbation), [[scGPT]] (embedding-level analyses); contrast with transcriptome-level [[GEARS]], [[CPA]], [[scGen]].

## Related concepts
[[in-silico perturbation]], [[perturbation prediction]], [[cell embedding]], [[cell state]], [[virtual cell model]]

## Tags
#concept #scfm #perturbation
