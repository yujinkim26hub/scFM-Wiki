---
title: tokenization or encoding strategy comparison
aliases: [tokenization or encoding strategy comparison]
type: comparison
criterion: tokenization or encoding strategy
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# tokenization or encoding strategy comparison

> Compares models on a **single shared criterion**: how genes and expression values are *tokenized / encoded* into model input. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
The representation strategy used to turn a cell into model input: **gene identity** tokens, **rank-based** expression ordering, **binned** expression values, **raw/continuous** values, **condition/perturbation** tokens, or **protein-embedding**-derived gene representations. This is one of the explicit-input-representation requirements in [[AGENTS]] §0.4.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Rank-based encoding of genes; no explicit expression-value tokens. | Theodoris 2023, Nature (needs verification) | Cell = ordered gene ranking; magnitude is implicit. | needs verification. |
| [[scGPT]] | Gene identity tokens + binned expression + condition tokens. | Cui 2024, Nat Methods (needs verification) | Combines identity, value bins, and condition signals. | Bin scheme details needs verification. |
| [[scFoundation]] | Raw continuous expression + read-depth (T/S) tokens. | Hao 2024, Nat Methods (needs verification) | Preserves continuous magnitude; T/S tokens encode read depth. | T/S token semantics needs verification. |
| [[scBERT]] | gene2vec gene embeddings + binned expression. | Yang 2022, Nat Mach Intell (needs verification) | Gene identity via pretrained gene2vec; values binned. | needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Encoding strategy needs verification. |
| [[CellPLM]] | Cells encoded as tokens; Gaussian-mixture latent prior. | Wen 2024, ICLR (needs verification) | Token unit is the cell, not the gene. | Per-gene encoding needs verification. |
| [[scPRINT]] | needs verification. | Kalfon ~2024 (needs verification) | needs verification. | Input encoding needs verification. |
| [[UCE]] | Genes via ESM2 protein-LM embeddings (vocabulary-free); cell = "cell sentence" of expressed genes sampled with replacement, weighted by expression. | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | Gene identity from protein sequence; expression enters via sampling frequency, not binned/raw value tokens. | Positional/genomic encoding details needs verification. |
| [[GeneCompass]] | Knowledge-informed priors (GRN, promoter, gene family, co-expression) folded into encoding. | Yang 2024 (needs verification) | Biological priors augment the gene representation. | Exact mechanism needs verification. |
| [[GEARS]] | Genes as nodes in co-expression + GO graph; perturbations as graph signals. | Roohani 2023, Nat Biotech (needs verification) | Graph-structured encoding, not token sequence. | needs verification. |
| [[CPA]] | Condition embeddings for perturbation / dose / covariate (additive latent). | Lotfollahi 2023, Mol Syst Biol (needs verification) | Conditions are disentangled embedding vectors. | needs verification. |
| [[scGen]] | Expression encoded into a VAE latent; conditions handled by vector arithmetic. | Lotfollahi 2019, Nat Methods (needs verification) | No discrete tokenization; latent-space representation. | needs verification. |

## Notes
- Rank ([[Geneformer]]), binned ([[scGPT]], [[scBERT]]), raw continuous ([[scFoundation]]), and protein-embedding ([[UCE]]) strategies make different information available to the model.
- Perturbation-specific models ([[GEARS]], [[CPA]], [[scGen]]) encode *conditions* explicitly rather than tokenizing genes for masked pretraining.

## Related
- [[input format comparison]] · [[architecture comparison]] · [[training objective comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #needs-verification
