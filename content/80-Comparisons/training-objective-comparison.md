---
title: training objective comparison
aliases: [training objective comparison]
type: comparison
criterion: training objective
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# training objective comparison

> Compares models on a **single shared criterion**: their *training objective(s)*. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
The loss / learning signal: masked gene prediction, generative modeling, contrastive learning, reconstruction, or supervised perturbation prediction. Distinguishing self-supervised pretraining objectives from supervised perturbation objectives is required by [[AGENTS]] §0.2 and §0.5.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Masked gene prediction (self-supervised). | Theodoris 2023, Nature (needs verification) | Learns context from masked ranked genes. | needs verification. |
| [[scGPT]] | Generative objective over expression (self-supervised pretraining). | Cui 2024, Nat Methods (needs verification) | Generates expression / masked values. | Exact objective formulation needs verification. |
| [[scFoundation]] | Self-supervised reconstruction with read-depth conditioning. | Hao 2024, Nat Methods (needs verification) | Reconstructs expression across read depths. | Exact objective needs verification. |
| [[scBERT]] | Masked-language-model-style objective over binned expression. | Yang 2022, Nat Mach Intell (needs verification) | BERT-style masking. | needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Objective needs verification. |
| [[CellPLM]] | Self-supervised with a Gaussian-mixture latent prior. | Wen 2024, ICLR (needs verification) | Latent-variable objective at the cell level. | Exact loss needs verification. |
| [[scPRINT]] | Multi-task objective (denoising / label / GRN). | Kalfon ~2024 (needs verification) | Combines several training signals. | Exact losses needs verification. |
| [[UCE]] | Self-supervised objective yielding universal embeddings. | Rosen 2023, bioRxiv (needs verification) | Produces embeddings without fine-tuning. | Exact objective needs verification. |
| [[GeneCompass]] | Self-supervised pretraining with knowledge-informed priors. | Yang 2024 (needs verification) | Priors regularize the pretraining loss. | Exact objective needs verification. |
| [[GEARS]] | Supervised perturbation prediction (regression to post-perturbation expression). | Roohani 2023, Nat Biotech (needs verification) | Trained directly on perturbation outcomes. | needs verification. |
| [[CPA]] | Supervised reconstruction with disentangled condition latent. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Learns additive perturbation/dose/covariate effects. | needs verification. |
| [[scGen]] | Supervised VAE reconstruction; response via latent arithmetic. | Lotfollahi 2019, Nat Methods (needs verification) | VAE reconstruction objective. | needs verification. |

## Notes
- Self-supervised objectives (masking, generation, reconstruction, contrastive) drive the general scFMs; supervised perturbation regression drives [[GEARS]], [[CPA]], [[scGen]].
- The objective constrains zero-shot vs fine-tuning behavior; see [[zero-shot capability comparison]] and [[fine-tuning capability comparison]].

## Related
- [[architecture comparison]] · [[pretraining data comparison]] · [[zero-shot capability comparison]] · [[perturbation capability comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #needs-verification
