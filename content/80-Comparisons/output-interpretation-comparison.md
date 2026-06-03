---
title: output interpretation comparison
aliases: [output interpretation comparison]
type: comparison
criterion: output interpretation
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# output interpretation comparison

> Compares models on a **single shared criterion**: how each model's output should be *interpreted biologically* — and what it does **not** mean. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
What kind of claim a model's output supports: a **cell-embedding shift**, a **classifier-score shift**, or a **true transcriptome-level (gene-expression) prediction** — these are different claims ([[AGENTS]] §0.3). An embedding shift is a movement in representation space, not a measured change in gene expression; only transcriptome-level outputs predict actual expression values. Do not infer biology beyond the source ([[AGENTS]] §0.7).

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | In-silico perturbation produces an embedding / cell-state shift. | Theodoris 2023, Nature (needs verification) | Output is a shift in representation space, not predicted expression values. | Does not yield a measured transcriptome change; needs verification. |
| [[scGPT]] | When fine-tuned on Perturb-seq, predicts transcriptome-level expression; embeddings otherwise. | Cui 2024, Nat Methods (needs verification) | Fine-tuned output can be read as predicted expression; frozen output is an embedding. | Zero-shot interpretation contested; needs verification. |
| [[scFoundation]] | Outputs embeddings; perturbation prediction only via [[GEARS]]. | Hao 2024, Nat Methods (needs verification) | Its own output is an embedding, not predicted expression. | needs verification. |
| [[scBERT]] | Classifier output = a label / score. | Yang 2022, Nat Mach Intell (needs verification) | A classifier-score shift is not an expression change. | needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Output interpretation needs verification. |
| [[CellPLM]] | Cell embeddings (and imputed expression). | Wen 2024, ICLR (needs verification) | Embeddings are representations; imputation fills missing values, not perturbation response. | needs verification. |
| [[scPRINT]] | Cell embeddings + GRN estimates. | Kalfon ~2024 (needs verification) | GRN edges are inferred associations, not validated causal links. | needs verification. |
| [[UCE]] | Cell embedding only. | Rosen 2023, bioRxiv (needs verification) | Embedding position reflects learned similarity, not expression. | needs verification. |
| [[GeneCompass]] | Gene + cell embeddings. | Yang 2024 (needs verification) | Embedding shift, not expression prediction. | needs verification. |
| [[GEARS]] | Predicted post-perturbation expression. | Roohani 2023, Nat Biotech (needs verification) | Output is a transcriptome-level prediction (actual expression values). | Predictive accuracy is dataset-dependent; needs verification. |
| [[CPA]] | Predicted expression under conditions. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Transcriptome-level prediction. | needs verification. |
| [[scGen]] | Predicted expression response. | Lotfollahi 2019, Nat Methods (needs verification) | Transcriptome-level prediction via latent arithmetic. | Generalization beyond observed responses needs verification. |

## Notes
- Key distinction: [[Geneformer]] in-silico perturbation = **embedding shift**; [[scBERT]] = **classifier-score**; [[GEARS]] / [[CPA]] / [[scGen]] (and fine-tuned [[scGPT]]) = **transcriptome-level prediction**.
- An embedding or classifier shift cannot be read as a measured gene-expression change ([[AGENTS]] §0.3, §0.7).

## Related
- [[model output comparison]] · [[perturbation capability comparison]] · [[zero-shot capability comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #needs-verification
