---
title: perturbation capability comparison
aliases: [perturbation capability comparison]
type: comparison
criterion: perturbation capability
tags: [comparison, scfm, perturbation, needs-verification]
status: stub
updated: 2026-06-03
---

# perturbation capability comparison

> Compares models on a **single shared criterion**: their *perturbation* capability — what kind of perturbation output, and how perturbation data are used. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
Two distinctions required by [[AGENTS]] §0.3 and §0.5: (a) whether perturbation output is an **embedding / cell-state shift** or a **transcriptome-level expression prediction**; and (b) whether perturbation data were used for **pretraining**, **fine-tuning**, **evaluation only**, or **not used**. General scFMs and perturbation-specific models are kept distinct.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | In-silico perturbation = embedding / cell-state shift; perturbation data not used in pretraining. | Theodoris 2023, Nature (needs verification) | Predicts a representation shift, not expression values. | Perturbation-data use needs verification. |
| [[scGPT]] | Fine-tuned on Perturb-seq → transcriptome-level prediction. | Cui 2024, Nat Methods (needs verification) | Perturbation data used for fine-tuning; output is predicted expression. | needs verification. |
| [[scFoundation]] | Perturbation handled by pairing with [[GEARS]], not by the model itself. | Hao 2024, Nat Methods (needs verification) | Provides embeddings into a downstream perturbation model. | needs verification. |
| [[scBERT]] | No native perturbation capability. | Yang 2022, Nat Mach Intell (needs verification) | Annotation-oriented; no perturbation output. | needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Perturbation capability needs verification. |
| [[CellPLM]] | Perturbation specifics needs verification. | Wen 2024, ICLR (needs verification) | Primarily annotation / imputation / spatial. | needs verification. |
| [[scPRINT]] | needs verification (GRN-focused, not perturbation prediction). | Kalfon ~2024 (needs verification) | Network inference rather than perturbation response. | needs verification. |
| [[UCE]] | No perturbation capability; perturbation data not used (pretrain/fine-tune/eval). | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | Embedding-only; neither in-silico embedding-shift nor transcriptome-level prediction. | — |
| [[GeneCompass]] | needs verification. | Yang 2024 (needs verification) | Embedding model; perturbation use unclear. | needs verification. |
| [[GEARS]] | Supervised on Perturb-seq; predicts post-perturbation expression, incl. unseen / combinatorial. | Roohani 2023, Nat Biotech (needs verification) | Transcriptome-level prediction; perturbation data used for training and eval. | needs verification. |
| [[CPA]] | Supervised; predicts expression for unseen condition / dose combos. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Transcriptome-level prediction; perturbation data used for training and eval. | needs verification. |
| [[scGen]] | Supervised; predicts expression response, generalizing to unobserved cell types. | Lotfollahi 2019, Nat Methods (needs verification) | Transcriptome-level prediction; perturbation/condition data used for training. | needs verification. |

## Notes
- **Embedding-shift** perturbation ([[Geneformer]]) and **transcriptome-level** prediction ([[GEARS]], [[CPA]], [[scGen]], fine-tuned [[scGPT]]) are different claims ([[AGENTS]] §0.3).
- [[scFoundation]] contributes embeddings to [[GEARS]] rather than predicting perturbations itself.
- Perturbation-data use: not used / pretraining-only for most general scFMs; fine-tuning for [[scGPT]]; core training + eval for [[GEARS]], [[CPA]], [[scGen]].

## Related
- [[output interpretation comparison]] · [[model output comparison]] · [[model type comparison]] · [[supported tasks comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #perturbation #needs-verification
