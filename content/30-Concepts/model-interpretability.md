---
title: model interpretability
aliases: [model interpretability, interpretability, attention analysis]
type: concept
tags: [concept, scfm, transformer]
status: stub
updated: 2026-06-03
---

# model interpretability

## Definition
Model interpretability is the set of methods used to explain what a trained model has learned or why it produced a given output. For [[single-cell foundation model|scFMs]] this commonly means **attention analysis**, [[in-silico perturbation]], and [[gene regulatory network|gene-network]] readouts from [[gene embedding|embeddings]].

## Why it matters for scFMs
Interpretability claims are how scFM papers connect black-box models to biology (e.g. "the model recovered known regulators"). Because these claims are easy to overstate, they require careful epistemic framing.

## How it works / key distinctions
- **Attention analysis:** inspecting attention weights between gene tokens to suggest [[gene relationship|gene relationships]] ([[scGPT]], [[Geneformer]]).
- **In-silico perturbation:** deleting/adding tokens and measuring [[cell-state shift|embedding shift]] to rank influential genes ([[Geneformer]]).
- **Embedding geometry:** clustering or neighbor structure of [[gene embedding|gene]]/[[cell embedding|cell]] embeddings.

## Common pitfalls / what it is not
- **Attention is not explanation, and not causation.** High attention or embedding proximity indicates statistical association in training data, not a mechanistic or causal link.
- Recovering "known" genes can be confounded by their abundance/prevalence in training data, not genuine mechanistic insight.
- An interpretability readout is a hypothesis generator; it requires independent (ideally interventional) validation.
- [[cell-state shift|Embedding shifts]] from in-silico perturbation are not transcriptome predictions ([[perturbation prediction]]).

## Models / methods that use it
- [[scGPT]] (attention-based gene networks), [[Geneformer]] (in-silico perturbation, network analysis), [[scPRINT]] ([[gene regulatory network]] outputs), [[GeneCompass]] (knowledge-informed).

## Related concepts
[[gene relationship]], [[gene regulatory network]], [[in-silico perturbation]], [[cell-state shift]], [[gene embedding]]

## Tags
#concept #scfm #transformer
