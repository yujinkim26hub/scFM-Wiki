---
title: gene embedding
aliases: [gene embedding, gene embeddings]
type: concept
tags: [concept, scfm]
status: stub
updated: 2026-06-03
---

# gene embedding

## Definition
A gene embedding is a learned vector that represents a gene in a continuous space, intended to capture aspects of the gene's expression context and its relationships to other genes. In [[single-cell foundation model|scFMs]], each gene is typically assigned a token whose embedding is learned during pretraining.

## Why it matters for scFMs
Gene embeddings are the input-level building blocks for most scFMs that use gene-identity tokens. They let the model attend over genes, support [[gene relationship]] and [[gene regulatory network]] readouts, and enable [[in-silico perturbation]] by adding/removing gene tokens. The geometry of the embedding space is sometimes interpreted as encoding functional similarity (needs verification of how faithfully).

## How it works / key distinctions
- A gene embedding is distinct from a [[cell embedding]]: the former represents a gene, the latter aggregates a cell's full profile.
- Some models learn gene embeddings purely from data ([[scBERT]], [[scGPT]]); others initialize from external knowledge ([[GeneCompass]] uses prior biological knowledge; [[UCE]] uses protein-sequence-derived gene representations) (needs verification of specifics).
- Whether two genes' embeddings being close implies a real biological relationship is an interpretation, not a guarantee.

## Common pitfalls / what it is not
- Embedding proximity is correlation/association at best, not [[gene regulatory network|regulatory]] or causal relationship.
- A gene embedding is not a measurement; it is a model parameter shaped by training data and objective.

## Models / methods that use it
- [[scBERT]], [[scGPT]], [[Geneformer]], [[scFoundation]], [[GeneCompass]] (knowledge-informed), [[UCE]] (sequence-informed), [[scPRINT]].

## Related concepts
[[cell embedding]], [[gene relationship]], [[gene regulatory network]], [[tokenization-strategy|tokenization strategy]], [[model interpretability]]

## Tags
#concept #scfm
