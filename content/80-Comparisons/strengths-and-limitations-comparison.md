---
title: strengths and limitations comparison
aliases: [strengths and limitations comparison]
type: comparison
criterion: strengths and limitations
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# strengths and limitations comparison

> Compares models on a **single shared criterion**: reported *strengths and limitations*. Do **not** rank models or declare a winner — record each model's reported strong points and caveats on its own terms, not relative to others. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
The design strengths and stated / inferred limitations of each model, as reported by its source. This is descriptive, not comparative scoring; no "better than" claims ([[AGENTS]] §0.9).

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Strength: rank-based encoding + large corpus; disease validation shown. | Theodoris 2023, Nature (needs verification) | Robust embeddings, in-silico perturbation as cell-state shift. | Limited batch integration; classification needs fine-tuning. |
| [[scGPT]] | Strength: broad task suite incl. fine-tuned perturbation and integration. | Cui 2024, Nat Methods (needs verification) | Versatile generative scFM. | Zero-shot performance contested. |
| [[scFoundation]] | Strength: raw-value input + read-depth tokens; large scale. | Hao 2024, Nat Methods (needs verification) | Strong feature backbone. | Relies on [[GEARS]] for perturbation; specifics needs verification. |
| [[scBERT]] | Strength: large gene vocabulary via Performer; strong annotation focus. | Yang 2022, Nat Mach Intell (needs verification) | Effective for cell-type annotation. | No native perturbation; integration not its focus. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | SSM backbone may offer efficiency. | Most specifics needs verification. |
| [[CellPLM]] | Strength: models inter-cell + spatial relations. | Wen 2024, ICLR (needs verification) | Cell-as-token + spatial context. | Perturbation specifics needs verification. |
| [[scPRINT]] | Strength: GRN inference + multi-task outputs. | Kalfon ~2024 (needs verification) | Network-oriented scFM. | Venue / backbone needs verification. |
| [[UCE]] | Strength: zero-shot, vocabulary-free, cross-species embeddings; protein-sequence gene grounding. | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | No fine-tuning required. | Embedding-only (no expression/perturbation); zero-shot-only may trail tuned models. |
| [[GeneCompass]] | Strength: knowledge-informed priors; cross-species. | Yang 2024 (needs verification) | Biological priors aid generalization. | Venue / cell count needs verification. |
| [[GEARS]] | Strength: transcriptome-level prediction incl. unseen / combinatorial perturbations. | Roohani 2023, Nat Biotech (needs verification) | Strong for genetic-perturbation outcomes. | Requires perturbation data; not a foundation model. |
| [[CPA]] | Strength: disentangled, interpretable condition latent; unseen combos. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Interpretable perturbation/dose effects. | Requires labeled conditions; not a foundation model. |
| [[scGen]] | Strength: simple VAE arithmetic generalizing response to new cell types. | Lotfollahi 2019, Nat Methods (needs verification) | Lightweight response prediction. | Requires labeled conditions; not a foundation model. |

## Notes
- Strengths/limitations are recorded per model on its own terms; this is not a ranking ([[AGENTS]] §0.9).
- General-scFM limitations often concern zero-shot reliability and integration; perturbation-specific-model limitations concern their dependence on labeled perturbation data.

## Related
- [[best use cases comparison]] · [[supported tasks comparison]] · [[zero-shot capability comparison]] · [[perturbation capability comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #needs-verification
