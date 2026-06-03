---
title: benchmark and validation comparison
aliases: [benchmark and validation comparison]
type: comparison
criterion: benchmark and validation
tags: [comparison, scfm, benchmark, needs-verification]
status: stub
updated: 2026-06-03
---

# benchmark and validation comparison

> Compares models on a **single shared criterion**: the *benchmarks and metrics* each source reports. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
The main benchmark tasks, datasets, and metrics reported by each model's source. Specific dataset names and metric values are heavily `needs verification` until summaries are ingested; this page records *what kind* of evaluation was reported, not comparative scores.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Evaluated on annotation, GRN, and in-silico perturbation tasks. | Theodoris 2023, Nature (needs verification) | Embedding-based evaluations. | Datasets / metrics needs verification. |
| [[scGPT]] | Evaluated on annotation, integration, multi-omic, GRN, perturbation. | Cui 2024, Nat Methods (needs verification) | Broad benchmark suite. | Datasets / metrics needs verification. |
| [[scFoundation]] | Evaluated on embedding-based tasks; perturbation via [[GEARS]]. | Hao 2024, Nat Methods (needs verification) | Benchmarks include downstream pairing. | Datasets / metrics needs verification. |
| [[scBERT]] | Evaluated on cell-type annotation. | Yang 2022, Nat Mach Intell (needs verification) | Annotation benchmarks. | Datasets / metrics needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Benchmarks needs verification. |
| [[CellPLM]] | Evaluated on annotation, imputation, spatial tasks. | Wen 2024, ICLR (needs verification) | Includes spatial benchmarks. | Datasets / metrics needs verification. |
| [[scPRINT]] | Evaluated on GRN inference and related multi-task outputs. | Kalfon ~2024 (needs verification) | GRN-focused evaluation. | Datasets / metrics needs verification. |
| [[UCE]] | Evaluated on zero-shot / cross-species cell-embedding tasks. | Rosen 2023, bioRxiv (needs verification) | Zero-shot embedding benchmarks. | Datasets / metrics needs verification. |
| [[GeneCompass]] | Evaluated on cross-species downstream tasks. | Yang 2024 (needs verification) | Human + mouse benchmarks. | Datasets / metrics needs verification. |
| [[GEARS]] | Evaluated on Perturb-seq perturbation prediction, incl. unseen / combinatorial. | Roohani 2023, Nat Biotech (needs verification) | Perturbation-prediction benchmarks. | Datasets / metrics needs verification. |
| [[CPA]] | Evaluated on perturbation / dose / covariate prediction. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Condition-prediction benchmarks. | Datasets / metrics needs verification. |
| [[scGen]] | Evaluated on perturbation-response prediction across cell types. | Lotfollahi 2019, Nat Methods (needs verification) | Response-prediction benchmarks. | Datasets / metrics needs verification. |

## Notes
- Benchmarks are not comparable across models without shared datasets and metrics; this page only records reported evaluation *types*.
- All specific dataset names and metric values are `needs verification` pending summary ingestion.

## Related
- [[supported tasks comparison]] · [[disease or biological validation comparison]] · [[perturbation capability comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #benchmark #needs-verification
