---
title: input format comparison
aliases: [input format comparison]
type: comparison
criterion: input format
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# input format comparison

> Compares models on a **single shared criterion**: the *input data format* they consume. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
What modality and form of single-cell data a model takes as input: scRNA / snRNA / scATAC / multi-omic; raw **counts** vs **normalized** expression; and the approximate number of **genes** in the input vocabulary. The *encoding* of those values is covered separately in [[tokenization or encoding strategy comparison]].

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | scRNA-seq expression; genes ranked by expression (no explicit value tokens). | Theodoris 2023, Nature (needs verification) | Input is rank order over genes, not raw counts. | Gene count needs verification. |
| [[scGPT]] | scRNA-seq; gene tokens + binned expression; also multi-omic settings reported. | Cui 2024, Nat Methods (needs verification) | Counts are binned before input. | Multi-omic scope / #genes needs verification. |
| [[scFoundation]] | scRNA-seq; raw continuous expression plus read-depth (T/S) tokens. | Hao 2024, Nat Methods (needs verification) | Consumes raw/continuous values directly. | #genes needs verification. |
| [[scBERT]] | scRNA-seq; binned expression over ~16–20k genes. | Yang 2022, Nat Mach Intell (needs verification) | Large gene vocabulary via Performer attention. | Exact #genes needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Modality and #genes needs verification. |
| [[CellPLM]] | scRNA-seq and spatial transcriptomics; cells treated as tokens. | Wen 2024, ICLR (needs verification) | Input includes spatial / inter-cell context. | Counts vs normalized needs verification. |
| [[scPRINT]] | scRNA-seq. | Kalfon ~2024 (needs verification) | needs verification. | Input encoding / #genes needs verification. |
| [[UCE]] | scRNA-seq/snRNA-seq counts, multi-species; genes mapped to ESM2 protein-LM embeddings. | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | Vocabulary-free: not tied to a fixed gene list. | — |
| [[GeneCompass]] | scRNA-seq, human + mouse. | Yang 2024 (needs verification) | Cross-species input. | #genes / form needs verification. |
| [[GEARS]] | Perturb-seq expression plus co-expression and GO graph structure. | Roohani 2023, Nat Biotech (needs verification) | Requires perturbation-labeled input. | needs verification. |
| [[CPA]] | Perturbation-labeled scRNA-seq with covariate/dose annotations. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Requires condition annotations. | Counts vs normalized needs verification. |
| [[scGen]] | scRNA-seq with condition labels. | Lotfollahi 2019, Nat Methods (needs verification) | Requires paired condition labels. | needs verification. |

## Notes
- Several models reduce expression to binned values ([[scGPT]], [[scBERT]]) or rank order ([[Geneformer]]) rather than feeding raw counts; [[scFoundation]] keeps raw continuous values. See [[tokenization or encoding strategy comparison]].
- [[UCE]] is vocabulary-free via protein-LM embeddings, so its input is not pinned to a fixed gene list.

## Related
- [[tokenization or encoding strategy comparison]] · [[architecture comparison]] · [[pretraining data comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #needs-verification
