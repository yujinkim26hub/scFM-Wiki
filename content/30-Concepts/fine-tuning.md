---
title: fine-tuning
aliases: [fine-tuning, fine-tune, finetuning]
type: concept
tags: [concept, scfm]
status: stub
updated: 2026-06-03
---

# fine-tuning

## Definition
Fine-tuning adapts a pretrained model to a specific downstream task by updating its parameters (often with an added task-specific head) using labeled data for that task. Unlike [[zero-shot prediction|zero-shot]] use, the model's weights change.

## Why it matters for scFMs
Most reported strong results for [[single-cell foundation model|scFMs]] on annotation, [[perturbation prediction]], or [[data integration]] come *after* fine-tuning, not zero-shot. This distinction is central to interpreting benchmark claims (AGENTS.md §0.2).

## How it works / key distinctions
- A task head (e.g. a classifier or regression decoder) is attached; some or all backbone layers are updated.
- **Full fine-tuning** updates all weights; **parameter-efficient** variants (e.g. adapters/LoRA-style) update few (needs verification of which scFMs use which).
- Fine-tuning for [[perturbation prediction]] (e.g. [[scGPT]]) yields transcriptome-level outputs; this is different from [[Geneformer]]'s embedding-shift, which need not involve fine-tuning.

## Common pitfalls / what it is not
- Fine-tuned performance must not be reported as [[zero-shot prediction|zero-shot]] capability.
- Fine-tuning requires labeled data; gains may come from the head/labels rather than the pretrained representation — controls (e.g. fine-tuning a random-init model) help isolate the contribution (needs verification per paper).
- Risk of overfitting and of data leakage between pretraining and evaluation.

## Models / methods that use it
- [[scGPT]], [[scBERT]], [[Geneformer]], [[scFoundation]], [[CellPLM]] all support task-specific fine-tuning.

## Related concepts
[[zero-shot prediction]], [[transfer learning]], [[perturbation prediction]], [[single-cell foundation model]]

## Tags
#concept #scfm #needs-verification
