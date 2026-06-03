---
title: model type comparison
aliases: [model type comparison]
type: comparison
criterion: model type
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# model type comparison

> Compares models on a **single shared criterion**: their model *type / class* (general scFM vs perturbation-specific vs other) and backbone family. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
Whether a model is a **general single-cell foundation model** (pretrained on large unlabeled atlases) or a **perturbation-specific model** (supervised on perturbation data; not a foundation model in the same sense), plus its backbone family. This distinction governs how every other capability claim should be read; see [[AGENTS]] §0.6.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | General scFM; encoder transformer backbone. | Theodoris 2023, Nature (needs verification) | Foundation-model class: pretrain then reuse embeddings / fine-tune. | Details pending summary ingestion. |
| [[scGPT]] | General scFM; generative transformer backbone. | Cui 2024, Nat Methods (needs verification) | Foundation-model class with generative head. | needs verification. |
| [[scFoundation]] | General scFM; xTrimoGene asymmetric encoder-decoder (~100M params). | Hao 2024, Nat Methods (needs verification) | Foundation-model class. | Param count needs verification. |
| [[scBERT]] | General scFM; BERT + Performer attention. | Yang 2022, Nat Mach Intell (needs verification) | Foundation-model class, oriented to annotation. | needs verification. |
| [[scMamba]] | General scFM; Mamba / state-space (SSM) backbone. | ~2024 (needs verification) | SSM-family foundation model. | Most specifics needs verification; multiple preprints may share the name. |
| [[CellPLM]] | General scFM; transformer treating cells as tokens. | Wen 2024, ICLR (needs verification) | Foundation-model class; cell-level / spatial. | needs verification. |
| [[scPRINT]] | General scFM focused on gene-network inference; multi-task. | Kalfon ~2024 (venue needs verification) | Foundation-model class with GRN emphasis. | Venue and backbone needs verification. |
| [[UCE]] | General scFM; protein-LM-conditioned, cross-species. | Rosen 2023, bioRxiv (needs verification) | Foundation-model class; universal embeddings. | needs verification. |
| [[GeneCompass]] | General scFM; knowledge-informed, cross-species. | Yang 2024 (venue needs verification) | Foundation-model class with biological priors. | Venue needs verification. |
| [[GEARS]] | Perturbation-specific model; GNN over co-expression + GO graph. | Roohani 2023, Nat Biotech (needs verification) | Supervised perturbation predictor, not a foundation model. | needs verification. |
| [[CPA]] | Perturbation-specific model; autoencoder with disentangled latent. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Supervised perturbation predictor, not a foundation model. | needs verification. |
| [[scGen]] | Perturbation-specific model; VAE + latent vector arithmetic. | Lotfollahi 2019, Nat Methods (needs verification) | Explicitly not a foundation model. | needs verification. |

## Notes
- Rows 1–9 are general scFMs; rows 10–12 are perturbation-specific. Capability claims must respect this boundary ([[AGENTS]] §0.6).
- Backbone families span transformer encoder/decoder, SSM/Mamba, GNN, and VAE; see [[architecture comparison]].

## Related
- [[architecture comparison]] · [[perturbation capability comparison]] · [[model comparison overview]] · [[Geneformer]] · [[GEARS]] · [[scGen]]

## Tags
#comparison #scfm #needs-verification
