---
title: best use cases comparison
aliases: [best use cases comparison]
type: comparison
criterion: best use cases
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# best use cases comparison

> Compares models on a **single shared criterion**: the *use cases* each is best suited to, as supported by its source. Do **not** rank models or declare a winner — "best use case" here means the task a model was designed/reported for, not a claim that it beats others. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
The use case each model is reported to fit, based on its design and supported tasks. This is a routing aid (which model for which question), not a performance ranking ([[AGENTS]] §0.9). Pick by task fit and capability class, not by an implied leaderboard.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Annotation, GRN, in-silico perturbation (cell-state shift). | Theodoris 2023, Nature (needs verification) | Use for embedding-based analysis and hypothesis-level perturbation shifts. | Not for transcriptome-level perturbation prediction. |
| [[scGPT]] | Annotation, integration, multi-omic, GRN, fine-tuned perturbation. | Cui 2024, Nat Methods (needs verification) | Use when a versatile, fine-tunable scFM is needed. | Zero-shot reliability contested. |
| [[scFoundation]] | Feature backbone; perturbation via [[GEARS]]. | Hao 2024, Nat Methods (needs verification) | Use as embeddings for downstream models. | Perturbation needs a paired model. |
| [[scBERT]] | Cell-type annotation. | Yang 2022, Nat Mach Intell (needs verification) | Use for supervised annotation. | No native perturbation / integration focus. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | Possibly efficiency-oriented use cases. | Most specifics needs verification. |
| [[CellPLM]] | Annotation, imputation, spatial analysis. | Wen 2024, ICLR (needs verification) | Use when inter-cell / spatial context matters. | Perturbation specifics needs verification. |
| [[scPRINT]] | Gene-network inference and denoising. | Kalfon ~2024 (needs verification) | Use for GRN-centric questions. | Venue / specifics needs verification. |
| [[UCE]] | Cross-species annotation, atlas/query mapping, dataset integration — zero-shot. | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | Use when no fine-tuning and cross-species/vocabulary-free generality are wanted. | Embedding-only; not for expression/perturbation. |
| [[GeneCompass]] | Cross-species embedding tasks with biological priors. | Yang 2024 (needs verification) | Use for human/mouse cross-species analysis. | Specifics needs verification. |
| [[GEARS]] | Predicting genetic perturbation outcomes, incl. unseen / combinatorial. | Roohani 2023, Nat Biotech (needs verification) | Use when perturbation data exist and expression prediction is the goal. | Requires perturbation data. |
| [[CPA]] | Predicting drug / dose / covariate response. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Use for compositional condition prediction. | Requires labeled conditions. |
| [[scGen]] | Generalizing a perturbation response to unobserved cell types. | Lotfollahi 2019, Nat Methods (needs verification) | Use for response transfer across cell types. | Requires labeled conditions. |

## Notes
- General scFMs suit embedding / annotation / integration / GRN questions; perturbation-specific models suit transcriptome-level perturbation prediction when labeled data exist.
- This page routes by task fit and capability class, not by performance; no "better than" claims ([[AGENTS]] §0.9).

## Related
- [[strengths and limitations comparison]] · [[supported tasks comparison]] · [[perturbation capability comparison]] · [[zero-shot capability comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #needs-verification
