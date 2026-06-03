---
title: gene regulatory network
aliases: [gene regulatory network, GRN, gene regulatory networks]
type: concept
tags: [concept, scfm]
status: stub
updated: 2026-06-03
---

# gene regulatory network

## Definition
A gene regulatory network (GRN) is a (typically directed) graph in which nodes are genes (or regulators such as transcription factors) and edges represent regulatory relationships — one gene's product influencing another gene's expression. GRNs encode directionality and, ideally, causality, unlike a [[gene relationship|co-expression]] graph.

## Why it matters for scFMs
GRN inference is a flagship application claimed for several [[single-cell foundation model|scFMs]]. The hope is that representations learned over many cells encode regulatory structure that can be extracted from attention or [[gene embedding|embeddings]], or perturbed via [[in-silico perturbation]] to reveal downstream effects.

## How it works / key distinctions
- [[scPRINT]] is explicitly designed for cell-type-specific GRN inference (needs verification of method details).
- [[Geneformer]] supports network-style analyses, including [[in-silico perturbation]] of regulators to observe predicted [[cell-state shift|state shifts]].
- A GRN is directed and aims at regulation; a co-expression network is undirected association. Do not equate them.

## Common pitfalls / what it is not
- **Correlation ≠ causation.** Edges derived from expression correlation or attention are candidate regulatory links, not established causal ones.
- An inferred GRN reflects the training data and objective; validation requires perturbation/interventional evidence.
- Strong attention between a TF and a target is not proof of regulation ([[model interpretability]]).

## Models / methods that use it
- [[scPRINT]] (GRN inference), [[Geneformer]] (network analysis, in-silico perturbation of regulators), [[scGPT]] (attention-based gene networks), [[GeneCompass]] (knowledge priors).

## Related concepts
[[gene relationship]], [[gene embedding]], [[in-silico perturbation]], [[model interpretability]]

## Tags
#concept #scfm #needs-verification
