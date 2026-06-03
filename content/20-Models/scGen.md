---
title: scGen
aliases: [scGen]
type: model
model_class: perturbation-specific
year: 2019
tags: [scfm, model, perturbation, vae, needs-verification]
status: stub
updated: 2026-06-03
---

# scGen

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
scGen is a **perturbation-specific model — NOT a pretrained [[single-cell foundation model]]** — and is the **earliest** of the perturbation models tracked here. Introduced by Lotfollahi et al., Nature Methods 2019, it combines a **variational autoencoder (VAE)** with **latent-space vector arithmetic** to predict cellular responses to a perturbation/stimulation. Its key result is generalizing an observed response (e.g. stimulation) to **cell types where that response was not observed** (out-of-distribution). It predates the scFM wave and requires labeled perturbation training data.

## 2. Original paper
Lotfollahi et al., 2019 — scGen, Nature Methods. summary: to be ingested.

## 3. Model type
**Supervised / generative perturbation model** (VAE + latent vector arithmetic). Perturbation-specific, not a foundation model.

## Input

### 4. Input format
scRNA-seq expression profiles for control and perturbed/stimulated conditions, with cell-type labels. Counts vs normalized: needs verification.

### 5. Tokenization or encoding strategy
No language-model tokenization and no [[condition token]]. The perturbation effect is captured as a **difference vector in VAE latent space** (mean shift between conditions); predictions are made by **adding** that latent vector to cells of a target cell type and decoding.

### 6. Pretraining data
**Not a pretrained foundation model.** The VAE is trained on the relevant expression data; perturbation responses are obtained via latent arithmetic rather than self-supervised pretraining on a large corpus.

## Processing / Architecture

### 7. Architecture
Variational autoencoder (encoder/decoder; depth / parameter count: needs verification).

### 8. Training objective
Standard VAE objective (reconstruction + KL); perturbation prediction is performed post hoc via latent vector arithmetic (exact details need verification).

### 9. Interpretability
The perturbation as a single latent "delta" vector is an interpretable representation of a response; transferability across cell types is the central demonstrated property. Specific analyses: needs verification.

## Output

### 10. Model output
A **predicted gene expression profile** for a target cell type under the perturbation/stimulation — a **transcriptome-level** prediction obtained by decoding the latent-arithmetic result.

### 11. Output interpretation
The output is a generated/predicted expression profile via latent vector arithmetic, not merely an embedding shift label or classifier score. It is a model prediction; accuracy depends on the assumption that the perturbation acts as an approximately consistent latent shift across cell types.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction. Do not overclaim.

### 12. Supported tasks
Predicting cellular response to perturbation/stimulation, including transfer of an observed response to **unobserved (out-of-distribution) cell types**.

### 13. Zero-shot capability
Not zero-shot in the scFM sense. It generalizes a response across cell types via latent arithmetic, but requires a trained VAE and an observed reference response.

### 14. Fine-tuning capability
Not applicable in the scFM fine-tuning sense.

### 15. Perturbation capability
**Core capability:** transcriptome-level [[perturbation prediction]] via latent vector arithmetic, with cross-cell-type generalization. Perturbation data use: **training / required** (a labeled reference response is needed). This is true expression prediction, distinct from scFM [[in silico perturbation]] embedding shifts.

### 16. Batch correction or integration capability
scGen's latent alignment has been applied to integration-style settings, but it is not primarily a [[batch correction]] / [[data integration]] method (needs verification).

## Evaluation

### 17. Benchmark and validation
Evaluated on stimulation/perturbation datasets with held-out cell types (exact datasets/metrics need verification). To be linked under [[Benchmarks]].

### 18. Disease or biological validation
Disease validation: needs verification. Do not overreach.

## Practical use

### 19. Strengths
Simple, interpretable latent-arithmetic approach; generalizes an observed perturbation response to unobserved cell types; foundational/early method.

### 20. Limitations
Requires labeled perturbation training data and an observed reference response; assumes a consistent latent shift; predates and is simpler than later models like [[CPA]] and [[GEARS]]; not a foundation model.

### 21. Best use cases
Predicting a known perturbation/stimulation response in cell types where it was not directly measured, given a reference response.

## Wiki links

### 22. Related models
[[CPA]], [[GEARS]], [[scGPT]], [[scFoundation]]

### 23. Related papers
Lotfollahi et al. 2019 (summary: to be ingested).

### 24. Tags
#scfm #model #perturbation #needs-verification
