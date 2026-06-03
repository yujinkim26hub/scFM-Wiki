---
title: transfer learning
aliases: [transfer learning]
type: concept
tags: [concept, scfm]
status: stub
updated: 2026-06-03
---

# transfer learning

## Definition
Transfer learning reuses representations learned on one (large, often unlabeled) task or dataset to improve performance on other tasks or datasets, typically with less task-specific data. It is the foundational premise behind [[single-cell foundation model|scFMs]].

## Why it matters for scFMs
The entire scFM proposition is transfer: pretrain self-supervised on broad single-cell atlases, then transfer to annotation, [[batch correction]], [[data integration]], [[gene regulatory network]] inference, and [[perturbation prediction]] — via [[zero-shot prediction|zero-shot]] embeddings or [[fine-tuning]].

## How it works / key distinctions
- **Zero-shot transfer:** frozen embeddings used directly ([[zero-shot prediction]]).
- **Fine-tuning transfer:** pretrained weights adapted with task labels ([[fine-tuning]]).
- Transfer can be across **tasks** (annotation → perturbation) and across **datasets/domains** (atlas → query; cross-tissue; cross-species, e.g. [[UCE]], [[GeneCompass]]).

## Common pitfalls / what it is not
- Transfer is an empirical claim, not a guarantee; pretraining can fail to help or even hurt vs simpler baselines (see [[zero-shot prediction]] caveats).
- Apparent transfer can be inflated by overlap/leakage between pretraining and evaluation data (needs verification per paper).
- Cross-species or cross-modality transfer is harder and should be claimed only with evidence.

## Models / methods that use it
- All general scFMs rely on it: [[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[UCE]], [[CellPLM]], [[scPRINT]], [[GeneCompass]], [[scMamba]].

## Related concepts
[[single-cell foundation model]], [[zero-shot prediction]], [[fine-tuning]], [[data integration]]

## Tags
#concept #scfm #needs-verification
