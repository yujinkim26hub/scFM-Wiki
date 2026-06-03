---
title: perturbation prediction
aliases: [perturbation prediction, transcriptional response prediction, transcriptome-level prediction, classifier-score shift]
type: concept
tags: [concept, scfm, perturbation]
status: stub
updated: 2026-06-03
---

# perturbation prediction

## Definition
Perturbation prediction is the task of predicting how a cell's molecular state changes in response to a perturbation (gene knockout/knockdown/overexpression, drug, cytokine). The critical question is *what kind of output* counts as the prediction.

## Why it matters for scFMs
It is one of the most overclaimed areas in the [[single-cell foundation model|scFM]] literature. Different models produce fundamentally different outputs, and conflating them inflates claims.

## How it works / key distinctions
Three distinct output types (AGENTS.md §0.3):

| Output type | What it predicts | Models |
|---|---|---|
| **Cell-embedding shift** | Movement in latent space — [[cell-state shift]] | [[Geneformer]] (in-silico perturbation) |
| **Classifier-score shift** | Change in a trained classifier's score (e.g. disease/state probability) | classifier-head analyses |
| **Transcriptome-level prediction** | Per-gene predicted expression after perturbation | [[GEARS]], [[CPA]], [[scGen]], [[scGPT]] (fine-tuned) |

- True transcriptome-level prediction requires perturbation data for training/fine-tuning and is evaluated against held-out measured responses (e.g. Perturb-seq).
- [[GEARS]], [[CPA]], [[scGen]] are perturbation-specific models; [[scGPT]] does it only after [[fine-tuning]]; [[Geneformer]] does embedding-shift, not expression prediction.

## Common pitfalls / what it is not
- An [[cell-state shift|embedding shift]] is **not** a transcriptome prediction. State this explicitly for any model.
- Predicting mean expression change is not the same as predicting single-cell distributions; check the metric.
- Strong benchmark numbers can hide reliance on perturbation-mean baselines; verify against simple controls (needs verification of specifics per paper).

## Models / methods that use it
- Transcriptome-level: [[GEARS]], [[CPA]], [[scGen]], [[scGPT]] (fine-tuned).
- Embedding-shift: [[Geneformer]].

## Related concepts
[[in-silico perturbation]], [[cell-state shift]], [[condition token]], [[fine-tuning]], [[cell embedding]]

## Tags
#concept #scfm #perturbation #needs-verification
