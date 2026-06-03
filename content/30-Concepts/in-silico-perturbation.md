---
title: in silico perturbation
aliases: [in silico perturbation, in-silico perturbation]
type: concept
tags: [concept, scfm, perturbation]
status: stub
updated: 2026-06-03
---

# in silico perturbation

## Definition
In-silico perturbation is the simulation of a genetic or chemical perturbation (e.g. gene deletion, overexpression, or activation) inside a model, to predict its effect without performing the wet-lab experiment. The form of the prediction depends entirely on the model.

## Why it matters for scFMs
It is a headline use case for [[single-cell foundation model|scFMs]], promising to prioritize targets or explain disease mechanisms computationally. But "perturbation" can mean very different outputs across models, which must be stated explicitly.

## How it works / key distinctions
Two broad styles — do not conflate them:

1. **Embedding-shift style** (e.g. [[Geneformer]]): remove or add a gene token, re-embed the cell, and measure the resulting [[cell-state shift]] in [[cell embedding|embedding]] space. Output is a *direction/magnitude in latent space*, not gene-level expression.
2. **Expression-prediction style** (e.g. [[GEARS]], [[scGPT]] fine-tuned for perturbation): predict the post-perturbation *transcriptome* (per-gene expression change). This is [[perturbation prediction]] at the expression level and requires perturbation training data.

[[CPA]] and [[scGen]] also predict expression-level responses but are perturbation-specific models, not general scFMs.

## Common pitfalls / what it is not
- An embedding-shift result is not a transcriptome prediction and should not be reported as one (AGENTS.md §0.3).
- Deleting a gene token is a model intervention; it does not guarantee the model's response matches real biology unless benchmarked against measured perturbation data.
- Apparent effects can reflect training-data correlations, not causal mechanism.

## Models / methods that use it
- Embedding-shift: [[Geneformer]].
- Expression-level: [[GEARS]], [[CPA]], [[scGen]], [[scGPT]] (fine-tuned).

## Related concepts
[[perturbation prediction]], [[cell-state shift]], [[gene regulatory network]], [[cell embedding]], [[condition token]]

## Tags
#concept #scfm #perturbation
