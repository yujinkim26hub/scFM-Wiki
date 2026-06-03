---
title: cell embedding
aliases: [cell embedding, cell embeddings]
type: concept
tags: [concept, scfm]
status: stub
updated: 2026-06-03
---

# cell embedding

## Definition
A cell embedding is a learned vector that summarizes a single cell's expression profile in a continuous low-dimensional space. In [[single-cell foundation model|scFMs]] it is typically produced by aggregating gene-level representations (e.g. a pooled or [CLS]-style output) for one cell.

## Why it matters for scFMs
Cell embeddings are the main output used for downstream tasks: cell-type annotation, clustering, [[batch correction]], [[data integration]], atlas mapping, and measuring [[cell-state shift]] in [[in-silico perturbation]]. The quality of an scFM is often judged by how well its cell embeddings support these tasks ([[zero-shot prediction|zero-shot]] or after [[fine-tuning]]).

## How it works / key distinctions
- A cell embedding is distinct from a [[gene embedding]] (gene-level) and from a transcriptome (a full vector of gene expression values).
- **An embedding is not a transcriptome.** It is a compressed representation; you cannot read off individual gene expression levels from it without a decoder, and many scFMs have no faithful decoder.
- Distances/shifts in embedding space describe representational change, not necessarily measured expression change.

## Common pitfalls / what it is not
- A [[cell-state shift|shift in cell-embedding space]] after a simulated perturbation is **not** a [[perturbation-prediction|transcriptome-level prediction]] of the response (AGENTS.md §0.3).
- Good clustering does not imply the embedding has preserved all biologically relevant signal; [[batch correction]] can over-mix and remove real variation.

## Models / methods that use it
- [[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[UCE]], [[CellPLM]], [[scPRINT]], [[GeneCompass]], [[scMamba]] all produce cell embeddings.

## Related concepts
[[gene embedding]], [[cell-state shift]], [[batch correction]], [[data integration]], [[in-silico perturbation]]

## Tags
#concept #scfm
