---
title: CPA
aliases: [CPA, Compositional Perturbation Autoencoder]
type: model
model_class: perturbation-specific
year: 2023
tags: [scfm, model, perturbation, autoencoder, needs-verification]
status: stub
updated: 2026-06-03
---

# CPA (Compositional Perturbation Autoencoder)

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
CPA ("Compositional Perturbation Autoencoder") is a **perturbation-specific model — NOT a pretrained [[single-cell foundation model]]**. Introduced by Lotfollahi et al., Molecular Systems Biology 2023, it is an autoencoder that **disentangles the latent space into additive components** for perturbation, dose, and covariates (e.g. cell type). Using condition/[[condition token]]-like embeddings, it can predict expression under **unseen combinations** of perturbation, dose, and covariate. It is trained **supervised** on perturbation data (drug and genetic).

## 2. Original paper
Lotfollahi et al., 2023 — "Compositional Perturbation Autoencoder" (CPA), Molecular Systems Biology. summary: to be ingested.

## 3. Model type
**Supervised perturbation-prediction / generative model** (autoencoder with disentangled latent space). Perturbation-specific, not a general scFM.

## Input

### 4. Input format
scRNA-seq expression profiles annotated with perturbation, dose, and covariate (e.g. cell type) labels. Counts vs normalized: needs verification. Supports drug and genetic perturbations.

### 5. Tokenization or encoding strategy
No language-model tokenization. Perturbation, dose, and covariates are encoded as **condition embeddings** (a [[condition token]]-like representation) that are combined **additively** in latent space. This compositional/additive structure is what enables generalization to unseen perturbation × dose × covariate combinations.

### 6. Pretraining data
**Not a pretrained foundation model.** Perturbation data are used for **supervised training**, not self-supervised pretraining.

## Processing / Architecture

### 7. Architecture
Autoencoder with an encoder/decoder and a **disentangled latent space** split into additive components for perturbation, dose, and covariates (parameter count / depth: needs verification). Adversarial disentanglement of latent factors (mechanism needs verification).

### 8. Training objective
Reconstruction of expression plus disentanglement of latent components (exact loss formulation, including any adversarial terms, needs verification).

### 9. Interpretability
The disentangled latent components (perturbation / dose / covariate) are interpretable axes; dose-response and covariate effects can be read off the latent structure. Specific analyses: needs verification.

## Output

### 10. Model output
A **predicted gene expression profile** under a specified (possibly unseen) combination of perturbation, dose, and covariate — a **transcriptome-level** prediction.

### 11. Output interpretation
The output is a generated/predicted expression profile, not just an embedding shift or classifier score. It is a model prediction conditioned on disentangled latent components and should be validated; reliability for far out-of-distribution combinations may vary.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction. Do not overclaim.

### 12. Supported tasks
[[perturbation prediction]] at transcriptome level for unseen combinations of perturbation, dose, and covariate (cell type); dose-response prediction.

### 13. Zero-shot capability
Not zero-shot in the scFM sense. It generalizes to **unseen combinations** of conditions seen individually during training, but requires a trained model.

### 14. Fine-tuning capability
Not applicable in the scFM fine-tuning sense; trained supervised on perturbation data rather than fine-tuned from a self-supervised checkpoint.

### 15. Perturbation capability
**Core capability:** transcriptome-level [[perturbation prediction]] across compositional perturbation/dose/covariate combinations, for both drug and genetic perturbations. Perturbation data use: **training (supervised)**.

### 16. Batch correction or integration capability
Covariates (incl. batch/cell type) are modeled as latent components, which can absorb covariate effects; this is not a general-purpose [[batch correction]] / [[data integration]] method (behavior needs verification).

## Evaluation

### 17. Benchmark and validation
Evaluated on drug and genetic perturbation datasets (exact datasets/metrics need verification). To be linked under [[Benchmarks]].

### 18. Disease or biological validation
Disease validation: needs verification (e.g. drug-response settings). Do not overreach.

## Practical use

### 19. Strengths
Disentangled, compositional latent space enabling prediction across unseen perturbation × dose × covariate combinations; handles drug and genetic perturbations and dose.

### 20. Limitations
Requires labeled perturbation training data; not a pretrained scFM; extrapolation reliability for novel combinations varies.

### 21. Best use cases
Predicting expression responses across doses, covariates, and combinations of known perturbations from labeled perturbation data.

## Wiki links

### 22. Related models
[[GEARS]], [[scGen]], [[scGPT]], [[scFoundation]]

### 23. Related papers
Lotfollahi et al. 2023 (summary: to be ingested).

### 24. Tags
#scfm #model #perturbation #needs-verification
