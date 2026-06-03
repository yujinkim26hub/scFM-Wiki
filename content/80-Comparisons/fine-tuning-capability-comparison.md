---
title: fine-tuning capability comparison
aliases: [fine-tuning capability comparison]
type: comparison
criterion: fine-tuning capability
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# fine-tuning capability comparison

> Compares models on a **single shared criterion**: what each requires **fine-tuning** for, and the typical task heads used. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
Which tasks need fine-tuning a pretrained model with a task head (vs frozen/zero-shot use), and what heads are typically attached (classifier, expression-generation, etc.). Fine-tuning is a capability class distinct from zero-shot and from supervised perturbation training ([[AGENTS]] §0.2).

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Classification requires fine-tuning a task head. | Theodoris 2023, Nature (needs verification) | Embeddings frozen; classifier fine-tuned on top. | Head specifics needs verification. |
| [[scGPT]] | Fine-tuned for annotation, integration, and perturbation (on Perturb-seq). | Cui 2024, Nat Methods (needs verification) | Fine-tuning unlocks transcriptome-level perturbation prediction. | needs verification. |
| [[scFoundation]] | Embeddings can be fine-tuned / paired with downstream models. | Hao 2024, Nat Methods (needs verification) | Used as a feature backbone. | Fine-tuning recipes needs verification. |
| [[scBERT]] | Fine-tuned with a classifier head for cell-type annotation. | Yang 2022, Nat Mach Intell (needs verification) | Annotation is the fine-tuned head. | needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Fine-tuning status needs verification. |
| [[CellPLM]] | Fine-tuned / decoded for annotation, imputation, spatial tasks. | Wen 2024, ICLR (needs verification) | Task-specific heads on cell embeddings. | needs verification. |
| [[scPRINT]] | Multi-task training covers denoising / label / GRN. | Kalfon ~2024 (needs verification) | Heads correspond to multiple tasks. | Fine-tuning vs joint-training needs verification. |
| [[UCE]] | None by design — authors state it is "not intended to be finetuned." | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | Used as a frozen, zero-shot embedder. | — |
| [[GeneCompass]] | Fine-tuned for downstream tasks (extent needs verification). | Yang 2024 (needs verification) | Pretrained backbone + task heads. | needs verification. |
| [[GEARS]] | n/a — trained directly (supervised) on perturbation data, not fine-tuned from a pretrained scFM. | Roohani 2023, Nat Biotech (needs verification) | Task-specific from the start. | — |
| [[CPA]] | n/a — trained directly on condition-labeled data. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Not a pretrain-then-fine-tune model. | — |
| [[scGen]] | n/a — trained directly as a supervised VAE. | Lotfollahi 2019, Nat Methods (needs verification) | Not a pretrain-then-fine-tune model. | — |

## Notes
- [[Geneformer]] and [[scBERT]] need fine-tuning for classification; [[scGPT]] needs fine-tuning for transcriptome-level perturbation; [[UCE]] is designed to avoid fine-tuning.
- Perturbation-specific models are supervised end-to-end rather than fine-tuned from a foundation model.

## Related
- [[zero-shot capability comparison]] · [[supported tasks comparison]] · [[perturbation capability comparison]] · [[training objective comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #needs-verification
