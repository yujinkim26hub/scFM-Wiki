---
title: expression value encoding
aliases: [expression value encoding, binned expression]
type: concept
tags: [concept, scfm, transformer]
status: stub
updated: 2026-06-03
---

# expression value encoding

## Definition
Expression value encoding is how a model represents the *magnitude* of a gene's expression (as opposed to the gene's identity). It is the second half of a [[tokenization-strategy|tokenization strategy]].

## Why it matters for scFMs
The encoding choice determines whether a model preserves, discretizes, or discards quantitative expression information — directly affecting what biology it can represent (AGENTS.md §0.4).

## How it works / key distinctions
| Scheme | What it preserves | Example models |
|---|---|---|
| **Binned expression** | Discretized magnitude (ordinal bins) | [[scGPT]], [[scBERT]] |
| **Raw / continuous value** | Full continuous magnitude | [[scFoundation]] |
| **Rank** | Relative order only, magnitude discarded | [[Geneformer]] — see [[rank-based encoding]] |

- Binning trades resolution for robustness to noise/normalization differences.
- Continuous encoding keeps magnitude but may be more sensitive to normalization and depth.
- Rank encoding is depth-robust but throws away magnitude entirely.

## Common pitfalls / what it is not
- Binned ≠ continuous: a binned model does not have access to exact expression values.
- Rank ([[rank-based encoding]]) is a *different* concept from value encoding — it encodes order, not magnitude.
- The number/spacing of bins is a hyperparameter that affects results (needs verification per model).

## Models / methods that use it
- Binned: [[scGPT]], [[scBERT]]. Continuous: [[scFoundation]]. Rank (contrast): [[Geneformer]].

## Related concepts
[[tokenization-strategy|tokenization strategy]], [[rank-based encoding]], [[gene embedding]], [[condition token]]

## Tags
#concept #scfm #transformer #needs-verification
