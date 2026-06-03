---
title: cell state
aliases: [cell state, cell states]
type: concept
tags: [concept, scfm]
status: stub
updated: 2026-06-03
---

# cell state

## Definition
A cell state is the current transcriptional (and broadly molecular) condition of a cell — what it is expressing now — which can change over time, with the cell cycle, signaling, stress, or perturbation. It is distinct from a fixed, discrete **cell type**: states often form a continuum.

## Why it matters for scFMs
[[single-cell foundation model|scFMs]] place cells in a learned [[cell embedding|embedding]] space where position is taken to reflect cell state. Tasks like annotation, trajectory analysis, and measuring [[cell-state shift]] under [[in-silico perturbation]] all depend on the embedding capturing meaningful state structure.

## How it works / key distinctions
- **Cell type vs cell state:** type is a relatively stable identity label (e.g. T cell); state is the dynamic condition (e.g. activated, cycling, stressed). The boundary is fuzzy and partly definitional.
- States are often continuous; discretizing into clusters is a modeling choice, not ground truth.

## Common pitfalls / what it is not
- A cluster or a label is not the same as a biologically defined state; it is an operational summary.
- A change in embedding position ([[cell-state shift]]) describes representational movement, not a measured transcriptome change.

## Models / methods that use it
- [[Geneformer]], [[scGPT]], [[scFoundation]], [[UCE]], [[CellPLM]] represent cell state via embeddings; perturbation tools [[GEARS]], [[CPA]], [[scGen]] model transitions between states.

## Related concepts
[[cell embedding]], [[cell-state shift]], [[in-silico perturbation]], [[perturbation prediction]]

## Tags
#concept #scfm
