---
title: perturbation prediction benchmark
aliases: [perturbation prediction benchmark, perturbation prediction, perturbation-prediction benchmark, perturbation response prediction]
type: benchmark
tags: [benchmark, scfm, perturbation]
status: stub
updated: 2026-06-03
---

# perturbation prediction benchmark

## Task definition
Predict the post-perturbation single-cell expression state (or the change relative to control) for a genetic or chemical perturbation, often for perturbations or combinations not seen during training. The precise output claim matters: a true **transcriptome-level prediction** (predicted expression / delta vector) is distinct from a predicted embedding shift or a classifier-score shift (AGENTS §0.3).

## Common datasets
- [[Perturb-seq datasets]] (Norman, Replogle, Adamson, Dixit; needs verification of exact splits).
- [[CROP-seq datasets]].
- Chemical/drug-perturbation atlases (e.g. sci-Plex; needs verification).

## Metrics
- Pearson correlation between predicted and measured mean expression (or delta from control), often computed on **top differentially expressed (DE) genes** as well as all genes.
- MSE/RMSE on expression or on the delta.
- Direction-of-change and DE-gene recovery metrics.
- Blind spots: all-gene Pearson is inflated by the many unchanged genes; the meaningful signal lives in DE genes. A model can score well by predicting "near control." Mean-level metrics ignore distributional/variance effects.

## How models are evaluated here
- **Supervised perturbation models** trained on perturbation data: [[GEARS]], [[CPA]], [[scGen]] — these produce transcriptome-level predictions and are the primary methods for this task.
- **scFM fine-tuning**: [[scGPT]] reports a perturbation-prediction setting via fine-tuning on Perturb-seq.
- Many general scFMs do **not** perform true transcriptome-level perturbation prediction out of the box; they may produce embedding shifts or in-silico perturbation signals, which are a different claim (needs verification per model).
- Always state: pretraining vs fine-tuning vs evaluation-only use of perturbation data.

## Models evaluated
- [[GEARS]] — combinatorial/unseen-perturbation prediction; uses gene-relationship priors.
- [[CPA]] — compositional perturbation autoencoder; disentangles perturbation/dose/covariate effects.
- [[scGen]] — latent-space arithmetic for perturbation response.
- [[scGPT]] — fine-tuned perturbation prediction (source/summary needed).

## Caveats
- Generalization regimes differ: unseen single perturbations vs unseen combinations vs unseen cell contexts — report which.
- Baselines (predicting control mean, or a linear/additive model) are strong; improvements should be measured against them.
- Cell-line-derived training limits biological generalization (see [[Perturb-seq datasets]]).
- Cross-paper metrics differ in gene sets and normalization, hurting comparability.

## Related
- [[gene relationship benchmark]]
- [[Perturb-seq datasets]], [[CROP-seq datasets]]
- [[GEARS]], [[CPA]], [[scGen]], [[scGPT]]

## Tags
#benchmark #scfm #perturbation
