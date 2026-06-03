---
title: zero-shot benchmark
aliases: [zero-shot benchmark, zero shot benchmark, zero-shot evaluation, frozen embedding benchmark]
type: benchmark
tags: [benchmark, scfm, zero-shot]
status: stub
updated: 2026-06-03
---

# zero-shot benchmark

## Task definition
Evaluate a pretrained scFM **without any task-specific weight updates**: take frozen embeddings (cell or gene) and apply a lightweight, untrained-on-the-model probe (clustering, kNN, logistic regression, nearest-reference) to a downstream task. Measures the intrinsic quality of the pretrained representation, in contrast to fine-tuned evaluation (AGENTS §0.2).

## Common datasets
- Annotated atlases: [[Tabula Sapiens]], [[Human Cell Atlas]], [[CELLxGENE Census]] subsets.
- Whatever the downstream task uses (annotation, integration, embedding sets).

## Metrics
- Task-dependent: ARI/NMI/ASW for [[cell embedding benchmark]]; accuracy/macro-F1 for [[cell type annotation benchmark]]; scIB metrics for [[batch correction benchmark]].
- Blind spot: a "zero-shot" number is only meaningful relative to a baseline; absolute scores are easy to over-read.

## How models are evaluated here
- By definition **zero-shot / frozen**: no scFM weights are updated. The probe may be trained (e.g. logistic regression on labels), but the foundation model is not.
- Must be reported separately from fine-tuned results; conflating them is a common error.

## Models evaluated
- [[scGPT]], [[Geneformer]], [[scFoundation]], [[UCE]], [[CellPLM]] — reported zero-shot/frozen-embedding results; per-paper protocol and dataset needs verification.
- Baselines: HVG + PCA, scVI, Harmony.

## Caveats
- Several reports find simpler baselines (e.g. HVG + PCA) are sometimes competitive with or better than frozen scFM embeddings on standard tasks (needs verification of specific claims/papers).
- "Zero-shot" is used inconsistently across papers (some train a probe, some don't; some lightly tune) — read the exact protocol.
- Preprocessing (gene selection, normalization) can dominate results and is often not held constant across methods.
- Leakage between pretraining corpus and evaluation data undermines the "unseen" premise.

## Related
- [[cell embedding benchmark]], [[cell type annotation benchmark]], [[batch correction benchmark]], [[biological conservation benchmark]]
- [[CELLxGENE Census]], [[Tabula Sapiens]]

## Tags
#benchmark #scfm #zero-shot
