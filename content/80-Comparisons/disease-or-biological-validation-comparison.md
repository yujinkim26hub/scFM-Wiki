---
title: disease or biological validation comparison
aliases: [disease or biological validation comparison]
type: comparison
criterion: disease or biological validation
tags: [comparison, scfm, neuro, needs-verification]
status: stub
updated: 2026-06-03
---

# disease or biological validation comparison

> Compares models on a **single shared criterion**: whether a *disease / biological validation* was shown, and any neuroscience relevance. Do **not** rank models or declare a winner. Do not infer biology beyond the source ([[AGENTS]] §0.7). Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
What disease-context or biological validation each source demonstrates (e.g., a specific disease application, mechanistic follow-up), and whether any neuroscience relevance is reported. Only claims the source actually makes are recorded.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Cardiomyopathy disease validation reported. | Theodoris 2023, Nature (needs verification) | Demonstrates a cardiac-disease application. | Neuro relevance not established; needs verification. |
| [[scGPT]] | needs verification. | Cui 2024, Nat Methods (needs verification) | Disease-specific validation unclear. | Neuro relevance needs verification. |
| [[scFoundation]] | needs verification. | Hao 2024, Nat Methods (needs verification) | Disease validation unclear. | needs verification. |
| [[scBERT]] | needs verification. | Yang 2022, Nat Mach Intell (needs verification) | Disease validation unclear. | needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | needs verification. |
| [[CellPLM]] | needs verification. | Wen 2024, ICLR (needs verification) | Disease validation unclear. | needs verification. |
| [[scPRINT]] | needs verification. | Kalfon ~2024 (needs verification) | Disease validation unclear. | needs verification. |
| [[UCE]] | Broad cell-biology focus; no disease-prediction claims (atlas mapping incl. Human Brain Cell Atlas). | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | No disease validation claimed; integration could aid disease-tissue annotation. | Do not infer clinical utility. |
| [[GeneCompass]] | needs verification. | Yang 2024 (needs verification) | Disease validation unclear. | needs verification. |
| [[GEARS]] | Perturbation prediction has clear genetic-screen / functional-genomics relevance; specific disease validation needs verification. | Roohani 2023, Nat Biotech (needs verification) | Predicting genetic perturbation outcomes is biology-relevant. | Specific disease claims needs verification. |
| [[CPA]] | Drug / dose-response modeling has pharmacology relevance; specific disease validation needs verification. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Condition-response modeling relevant to drug effects. | needs verification. |
| [[scGen]] | Models perturbation response across cell types; specific disease validation needs verification. | Lotfollahi 2019, Nat Methods (needs verification) | Response-generalization is biologically motivated. | needs verification. |

## Notes
- Only [[Geneformer]] has a concrete disease validation seeded here (cardiomyopathy); all other disease claims are `needs verification`.
- Neuroscience relevance is unestablished across the board pending source ingestion; do not infer it ([[AGENTS]] §0.7).

## Related
- [[benchmark and validation comparison]] · [[perturbation capability comparison]] · [[best use cases comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #neuro #needs-verification
