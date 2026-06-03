---
title: batch correction or integration capability comparison
aliases: [batch correction or integration capability comparison]
type: comparison
criterion: batch correction or integration capability
tags: [comparison, scfm, batch-correction, needs-verification]
status: stub
updated: 2026-06-03
---

# batch correction or integration capability comparison

> Compares models on a **single shared criterion**: their *batch correction / data integration* capability. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
Whether a model is reported to perform batch correction or cross-dataset integration, and under what setting (frozen embeddings vs fine-tuned). Capability claims must be source-backed ([[AGENTS]] §0.1).

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Batch integration reported as limited. | Theodoris 2023, Nature (needs verification) | Not a primary strength. | needs verification. |
| [[scGPT]] | Supports batch correction (in a fine-tuned setting). | Cui 2024, Nat Methods (needs verification) | Integration via fine-tuning. | needs verification. |
| [[scFoundation]] | needs verification. | Hao 2024, Nat Methods (needs verification) | Embeddings may aid integration. | needs verification. |
| [[scBERT]] | Integration is not its focus. | Yang 2022, Nat Mach Intell (needs verification) | Annotation-oriented. | needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Integration capability needs verification. |
| [[CellPLM]] | needs verification (models inter-cell / spatial relations). | Wen 2024, ICLR (needs verification) | Cell-context modeling may support integration. | needs verification. |
| [[scPRINT]] | needs verification. | Kalfon ~2024 (needs verification) | GRN-focused; integration unclear. | needs verification. |
| [[UCE]] | Zero-shot integration of datasets, batches, and species; evaluated with scIB. | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | Embedding-level integration (not generative expression correction). | Exact scIB scores needs verification. |
| [[GeneCompass]] | Cross-species embeddings; integration extent needs verification. | Yang 2024 (needs verification) | Cross-species representation. | needs verification. |
| [[GEARS]] | n/a — perturbation-specific; integration not its purpose. | Roohani 2023, Nat Biotech (needs verification) | Out of scope. | — |
| [[CPA]] | Models covariate effects, which can absorb some batch structure; not a general integrator. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Covariate disentanglement is related but not the same as batch integration. | needs verification. |
| [[scGen]] | n/a — perturbation-specific; integration not its purpose. | Lotfollahi 2019, Nat Methods (needs verification) | Out of scope. | — |

## Notes
- [[scGPT]] reports batch correction in a fine-tuned setting; [[Geneformer]] reports it as limited; [[UCE]]/[[GeneCompass]] target cross-species representations.
- [[CPA]]'s covariate disentanglement is adjacent to but distinct from general batch integration.

## Related
- [[supported tasks comparison]] · [[zero-shot capability comparison]] · [[model output comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #batch-correction #needs-verification
