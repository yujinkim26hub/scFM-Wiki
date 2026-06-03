---
title: supported tasks comparison
aliases: [supported tasks comparison]
type: comparison
criterion: supported tasks
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# supported tasks comparison

> Compares models on a **single shared criterion**: the *downstream tasks* each is reported to support. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
Which tasks a model is reported (by its source) to perform: cell-type **annotation**, batch **integration**, **GRN** inference, **perturbation** prediction, imputation, multi-omic, spatial, etc. Capability claims must be source-backed ([[AGENTS]] §0.1).

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Annotation, GRN, in-silico perturbation. | Theodoris 2023, Nature (needs verification) | Embedding-based tasks; perturbation = cell-state shift. | needs verification. |
| [[scGPT]] | Annotation, integration, multi-omic, GRN, perturbation (fine-tuned). | Cui 2024, Nat Methods (needs verification) | Broad task suite via fine-tuning. | needs verification. |
| [[scFoundation]] | Embedding-based tasks; perturbation via [[GEARS]] pairing. | Hao 2024, Nat Methods (needs verification) | Perturbation not done by the model alone. | Full task list needs verification. |
| [[scBERT]] | Cell-type annotation (main task). | Yang 2022, Nat Mach Intell (needs verification) | Oriented to annotation. | Other tasks needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Task list needs verification. |
| [[CellPLM]] | Annotation, imputation, spatial tasks. | Wen 2024, ICLR (needs verification) | Includes spatial / cell-level tasks. | Perturbation specifics needs verification. |
| [[scPRINT]] | GRN inference, denoising, labeling (multi-task). | Kalfon ~2024 (needs verification) | GRN-focused multi-task scFM. | needs verification. |
| [[UCE]] | Zero-shot cell embedding (e.g., annotation via embeddings, cross-species). | Rosen 2023, bioRxiv (needs verification) | Embedding tasks without fine-tuning. | needs verification. |
| [[GeneCompass]] | Embedding-based tasks across human + mouse. | Yang 2024 (needs verification) | Cross-species downstream tasks. | Full task list needs verification. |
| [[GEARS]] | Perturbation prediction, incl. unseen / combinatorial. | Roohani 2023, Nat Biotech (needs verification) | Single-purpose: perturbation outcomes. | needs verification. |
| [[CPA]] | Perturbation / dose / covariate response prediction. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Predicts unseen condition combos. | needs verification. |
| [[scGen]] | Perturbation response prediction across cell types. | Lotfollahi 2019, Nat Methods (needs verification) | Generalizes observed response to new cell types. | needs verification. |

## Notes
- General scFMs cluster around annotation / integration / GRN / embedding tasks; perturbation-specific models ([[GEARS]], [[CPA]], [[scGen]]) target perturbation response only.
- Several tasks require fine-tuning rather than frozen use; see [[zero-shot capability comparison]] and [[fine-tuning capability comparison]].

## Related
- [[zero-shot capability comparison]] · [[fine-tuning capability comparison]] · [[perturbation capability comparison]] · [[batch correction or integration capability comparison]] · [[best use cases comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #needs-verification
