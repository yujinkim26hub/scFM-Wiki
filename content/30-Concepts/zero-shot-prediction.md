---
title: zero-shot prediction
aliases: [zero-shot prediction, zero-shot, zero-shot analysis]
type: concept
tags: [concept, scfm, zero-shot]
status: stub
updated: 2026-06-03
---

# zero-shot prediction

## Definition
Zero-shot prediction uses a pretrained model — or its frozen [[gene embedding|gene]]/[[cell embedding|cell]] embeddings — directly on a new task or dataset, with **no task-specific training and no parameter updates**. The model's weights are frozen; only the embeddings (or its native outputs) are consumed by a downstream, non-trained procedure (e.g. clustering, nearest-neighbor labeling).

## Why it matters for scFMs
Zero-shot is the strongest test of the [[single-cell foundation model|scFM]] / [[transfer learning]] premise: if pretraining learned general biology, frozen embeddings should perform well out of the box. It is the cleanest comparison to simpler baselines (HVG+PCA, scVI).

## How it works / key distinctions
- **Zero-shot** (frozen, no training) vs **[[fine-tuning]]** (weights updated with task labels) vs **supervised [[perturbation prediction]]** (trained on perturbation data) — keep these three classes separate (AGENTS.md §0.2).
- Zero-shot can still involve a non-parametric step (k-NN, clustering) downstream; that does not count as training the model.

## Common pitfalls / what it is not
- "Zero-shot" with any gradient update to the backbone is not zero-shot — it is [[fine-tuning]].
- Independent benchmarks report **mixed** zero-shot results for scFMs: in several integration/annotation settings, simpler baselines match or beat them (needs verification of specifics, e.g. Kedzierska et al.; Boiarsky et al.).
- Good zero-shot performance on one task does not transfer to all tasks.

## Models / methods that use it
- Zero-shot embedding use evaluated for [[Geneformer]], [[scGPT]], [[scFoundation]], [[UCE]], [[scBERT]] (results vary by benchmark; needs verification).

## Related concepts
[[fine-tuning]], [[transfer learning]], [[cell embedding]], [[data integration]], [[batch correction]]

## Tags
#concept #scfm #zero-shot #needs-verification
