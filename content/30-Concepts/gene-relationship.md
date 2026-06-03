---
title: gene relationship
aliases: [gene relationship, gene-gene interaction, gene relationships]
type: concept
tags: [concept, scfm]
status: stub
updated: 2026-06-03
---

# gene relationship

## Definition
A gene relationship is any association between two or more genes. Crucially, "relationship" covers several distinct kinds of link that are easy to conflate: statistical **co-expression**, **regulatory** relationship (one gene controlling another's expression), and **physical interaction** (e.g. protein-protein binding or DNA binding).

## Why it matters for scFMs
[[single-cell foundation model|scFMs]] are often claimed to "learn gene relationships" via [[gene embedding|gene embeddings]] and attention. What they can actually recover is mostly co-expression structure and, with care, candidate regulatory links. Distinguishing these is essential to avoid overclaiming.

## How it works / key distinctions
| Kind | What it means | What models can suggest |
|---|---|---|
| Co-expression | Correlated expression across cells | Readily captured by embeddings/attention |
| Regulatory | One gene modulates another (directional) | At best candidate, needs causal validation — see [[gene regulatory network]] |
| Physical | Direct molecular interaction (PPI, TF-DNA) | Generally not directly observable from expression alone |

- Attention weights and embedding proximity reflect statistical association in the training data, not mechanism.

## Common pitfalls / what it is not
- Co-expression is **not** regulation, and neither is necessarily a physical interaction.
- "The model attends strongly between gene A and B" is **not** evidence of a causal or physical link ([[model interpretability]]: attention is not explanation).
- Directionality and causality require interventional data, not correlations.

## Models / methods that use it
- [[scGPT]], [[Geneformer]] (attention-based gene relationship readouts), [[scPRINT]] (designed for network inference), [[GeneCompass]] (knowledge-informed).

## Related concepts
[[gene regulatory network]], [[gene embedding]], [[model interpretability]], [[in-silico perturbation]]

## Tags
#concept #scfm
