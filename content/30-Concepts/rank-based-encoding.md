---
title: rank-based encoding
aliases: [rank-based encoding, rank value encoding, rank-value encoding]
type: concept
tags: [concept, scfm, transformer]
status: stub
updated: 2026-06-03
---

# rank-based encoding

## Definition
Rank-based encoding represents a cell by **ordering its genes by expression level** and feeding the model that ranked sequence of gene tokens, rather than the numeric expression values. It is the encoding introduced by [[Geneformer]] ("rank value encoding").

## Why it matters for scFMs
It is a distinctive [[tokenization-strategy|tokenization]] choice that contrasts sharply with [[expression value encoding|binned]] or continuous-value approaches. Understanding it clarifies what [[Geneformer]] can and cannot see.

## How it works / key distinctions
- Genes in a cell are sorted by (normalized) expression; the model receives the ordered list of gene-identity tokens, often truncated to the top-N genes.
- Normalization (e.g. by a gene's typical expression across the corpus) is applied before ranking so that cell-type-distinguishing genes rise in rank (needs verification of exact scheme).
- **Magnitude is discarded:** only relative ordering remains.

## Common pitfalls / what it is not
- Rank encoding is **not** [[expression value encoding]]: it does not carry how much a gene is expressed, only its position in the ordering.
- Two cells with very different absolute expression but the same ordering look identical to the model.
- Truncation to top-N means low-ranked genes are dropped from the input.
- Pro: robust to sequencing depth and some normalization differences. Con: loses quantitative dynamic range.

## Models / methods that use it
- [[Geneformer]] (rank value encoding). Contrast: [[scGPT]]/[[scBERT]] (binned), [[scFoundation]] (continuous).

## Related concepts
[[tokenization-strategy|tokenization strategy]], [[expression value encoding]], [[gene embedding]]

## Tags
#concept #scfm #transformer #needs-verification
