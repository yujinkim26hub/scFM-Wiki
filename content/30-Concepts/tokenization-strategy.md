---
title: tokenization strategy
aliases: [tokenization strategy, tokenization]
type: concept
tags: [concept, scfm, transformer]
status: stub
updated: 2026-06-03
---

# tokenization strategy

## Definition
A tokenization strategy is the procedure that turns a single cell's expression profile into the sequence of input tokens a model consumes. For [[single-cell foundation model|scFMs]] this involves two choices: (1) how **gene identity** is represented, and (2) how **expression magnitude/order** is represented.

## Why it matters for scFMs
Tokenization is one of the largest design differences between scFMs and strongly shapes what the model can encode (AGENTS.md §0.4). Two models with similar architectures can behave very differently because of it.

## How it works / key distinctions
**Gene identity:** typically a learned [[gene embedding]] per gene (a gene-identity token).

**Expression representation** (see [[expression value encoding]]):
| Scheme | Idea | Example |
|---|---|---|
| [[rank-based encoding]] | Order genes by expression; use rank, discard magnitude | [[Geneformer]] |
| Binned expression | Discretize expression into bins → tokens | [[scGPT]], [[scBERT]] |
| Raw/continuous value | Feed continuous expression directly | [[scFoundation]] |
| [[condition token|Condition/metadata tokens]] | Special tokens for batch/perturbation/modality | [[scGPT]], [[CPA]] |

Some models add [[condition token|condition tokens]], metadata tokens, or multi-omic inputs.

## Common pitfalls / what it is not
- Tokenization is not just "preprocessing": it determines what information (e.g. expression magnitude) is even available to the model. [[rank-based encoding]] discards magnitude.
- Do not assume all scFMs see continuous expression; many see ranks or bins.
- Token vocabulary is restricted to the gene set seen in training; unseen genes need handling.

## Models / methods that use it
- [[Geneformer]] (rank), [[scGPT]]/[[scBERT]] (binned), [[scFoundation]] (continuous), [[UCE]], [[CellPLM]], [[GeneCompass]], [[scMamba]] (varied; needs verification).

## Related concepts
[[expression value encoding]], [[rank-based encoding]], [[condition token]], [[gene embedding]]

## Tags
#concept #scfm #transformer #needs-verification
