---
title: model output comparison
aliases: [model output comparison]
type: comparison
criterion: model output
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# model output comparison

> Compares models on a **single shared criterion**: what they *output*. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
The native output of each model: **gene embedding**, **cell embedding**, **predicted expression** (transcriptome-level), **class label**, or **GRN / gene-gene estimates**. Distinguishing these output types is required by [[AGENTS]] §0.3. How to interpret them biologically is covered in [[output interpretation comparison]].

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Gene + cell embeddings. | Theodoris 2023, Nature (needs verification) | Embedding model; classification added via fine-tuning. | needs verification. |
| [[scGPT]] | Embeddings + generated expression. | Cui 2024, Nat Methods (needs verification) | Can emit both embeddings and expression. | needs verification. |
| [[scFoundation]] | Cell / gene embeddings. | Hao 2024, Nat Methods (needs verification) | Embedding model; perturbation via [[GEARS]] pairing. | needs verification. |
| [[scBERT]] | Class label (cell type) via classifier head. | Yang 2022, Nat Mach Intell (needs verification) | Primary output is a label. | Embedding reuse needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Output type needs verification. |
| [[CellPLM]] | Cell embeddings. | Wen 2024, ICLR (needs verification) | Cell-level representations; supports imputation. | needs verification. |
| [[scPRINT]] | Cell embeddings + GRN / gene-gene estimates. | Kalfon ~2024 (needs verification) | Outputs network estimates alongside embeddings. | needs verification. |
| [[UCE]] | Universal cell embedding only (no expression output). | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | One vector per cell, comparable across datasets/species. | Exact dim (commonly 1280) needs verification. |
| [[GeneCompass]] | Gene + cell embeddings. | Yang 2024 (needs verification) | Embedding model. | needs verification. |
| [[GEARS]] | Predicted post-perturbation expression (transcriptome-level). | Roohani 2023, Nat Biotech (needs verification) | Outputs full expression profiles. | needs verification. |
| [[CPA]] | Predicted expression for conditions / combos. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Outputs expression under specified conditions. | needs verification. |
| [[scGen]] | Predicted expression response. | Lotfollahi 2019, Nat Methods (needs verification) | Outputs predicted response profiles. | needs verification. |

## Notes
- Most general scFMs primarily output embeddings; [[scBERT]] is oriented to label output; [[scPRINT]] additionally outputs GRN estimates.
- Only [[scGPT]] (among general scFMs, when fine-tuned) and the perturbation-specific models ([[GEARS]], [[CPA]], [[scGen]]) output transcriptome-level expression. See [[output interpretation comparison]].

## Related
- [[output interpretation comparison]] · [[architecture comparison]] · [[supported tasks comparison]] · [[perturbation capability comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #needs-verification
