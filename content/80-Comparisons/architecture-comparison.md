---
title: architecture comparison
aliases: [architecture comparison]
type: comparison
criterion: architecture
tags: [comparison, scfm, transformer, needs-verification]
status: stub
updated: 2026-06-03
---

# architecture comparison

> Compares models on a **single shared criterion**: their *neural architecture / backbone*. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
The backbone family and structure: transformer encoder / decoder, state-space model (SSM/Mamba), graph neural network (GNN), or variational autoencoder (VAE); plus depth / parameter count where reported. Param counts are `needs verification` per the seed caveats.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Encoder-only transformer. | Theodoris 2023, Nature (needs verification) | BERT-style encoder over ranked genes. | Depth / params needs verification. |
| [[scGPT]] | Generative transformer. | Cui 2024, Nat Methods (needs verification) | Decoder-style generation of expression. | Depth / params needs verification. |
| [[scFoundation]] | xTrimoGene asymmetric encoder-decoder; ~100M params. | Hao 2024, Nat Methods (needs verification) | Asymmetric design for scalability. | Param count needs verification. |
| [[scBERT]] | BERT with Performer (linear-attention) over ~16–20k genes. | Yang 2022, Nat Mach Intell (needs verification) | Performer attention enables large gene vocabulary. | Depth / params needs verification. |
| [[scMamba]] | Mamba / state-space (SSM) backbone. | ~2024 (needs verification) | SSM alternative to attention. | Most specifics needs verification; name may be shared by multiple preprints. |
| [[CellPLM]] | Transformer treating cells as tokens; Gaussian-mixture latent prior. | Wen 2024, ICLR (needs verification) | Models inter-cell / spatial relations. | Depth / params needs verification. |
| [[scPRINT]] | needs verification. | Kalfon ~2024 (needs verification) | Multi-task scFM. | Backbone / depth needs verification. |
| [[UCE]] | Transformer over protein-LM (ESM2) gene embeddings. | Rosen 2023, bioRxiv (needs verification) | Gene representations come from a protein LM. | Depth / params needs verification. |
| [[GeneCompass]] | Transformer with knowledge-informed priors. | Yang 2024 (needs verification) | Priors injected into a transformer backbone. | Depth / params needs verification. |
| [[GEARS]] | Graph neural network over co-expression + GO graph. | Roohani 2023, Nat Biotech (needs verification) | GNN, not a sequence model. | Depth / params needs verification. |
| [[CPA]] | Autoencoder with disentangled additive latent space. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Encoder-decoder with condition disentanglement. | needs verification. |
| [[scGen]] | Variational autoencoder (VAE) + latent vector arithmetic. | Lotfollahi 2019, Nat Methods (needs verification) | VAE latent supports response arithmetic. | needs verification. |

## Notes
- Backbones span transformer encoder ([[Geneformer]], [[scBERT]]), generative/asymmetric transformer ([[scGPT]], [[scFoundation]]), SSM ([[scMamba]]), GNN ([[GEARS]]), and VAE/autoencoder ([[scGen]], [[CPA]]).
- Architecture shapes the available output types; see [[model output comparison]].

## Related
- [[model type comparison]] · [[tokenization or encoding strategy comparison]] · [[training objective comparison]] · [[model output comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #transformer #needs-verification
