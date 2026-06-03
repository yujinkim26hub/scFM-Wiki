---
title: pretraining data comparison
aliases: [pretraining data comparison]
type: comparison
criterion: pretraining data
tags: [comparison, scfm, dataset, needs-verification]
status: stub
updated: 2026-06-03
---

# pretraining data comparison

> Compares models on a **single shared criterion**: the *pretraining corpus* used. Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
The unlabeled corpus a general scFM was pretrained on: corpus name, approximate number of **cells**, and source atlas. Perturbation-specific models that are supervised (not pretrained) get an "n/a" row with the reason. Exact cell/param counts are treated as `needs verification` per the seed caveats.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Genecorpus-30M; ~30M cells. | Theodoris 2023, Nature (needs verification) | Large human single-cell corpus. | Exact cell count needs verification. |
| [[scGPT]] | CELLxGENE-derived; ~33M cells. | Cui 2024, Nat Methods (needs verification) | Drawn from the CELLxGENE atlas. | Exact cell count needs verification. |
| [[scFoundation]] | ~50M cells. | Hao 2024, Nat Methods (needs verification) | Large-scale pretraining. | Corpus name / exact count needs verification. |
| [[scBERT]] | PanglaoDB; ~1M+ cells. | Yang 2022, Nat Mach Intell (needs verification) | Smaller corpus than later scFMs. | Exact count needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Corpus and cell count needs verification. |
| [[CellPLM]] | scRNA-seq + spatial data used for pretraining. | Wen 2024, ICLR (needs verification) | Includes spatial transcriptomic data. | Corpus name / cell count needs verification. |
| [[scPRINT]] | needs verification. | Kalfon ~2024 (needs verification) | needs verification. | Corpus and cell count needs verification. |
| [[UCE]] | ~36M single-cell transcriptomes across 8 species (human, mouse, zebrafish, lemur, 2 macaques, frog, pig); Integrated Mega-scale Atlas (IMA). | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | Cross-species self-supervised pretraining; perturbation data not used. | Exact dataset count needs verification. |
| [[GeneCompass]] | Human + mouse; ~120M cells. | Yang 2024 (needs verification) | Cross-species, knowledge-informed pretraining. | Cell count needs verification. |
| [[GEARS]] | n/a — supervised on Perturb-seq, not pretrained on an unlabeled corpus. | Roohani 2023, Nat Biotech (needs verification) | Perturbation-specific; trains on labeled perturbation data. | — |
| [[CPA]] | n/a — supervised on perturbation data, not pretrained on an unlabeled corpus. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Perturbation-specific. | — |
| [[scGen]] | n/a — supervised VAE, not pretrained on an unlabeled corpus. | Lotfollahi 2019, Nat Methods (needs verification) | Perturbation-specific; not a foundation model. | — |

## Notes
- Corpus scale ranges from ~1M+ ([[scBERT]]) to ~120M ([[GeneCompass]]) cells (all `needs verification`); raw counts alone do not imply quality or downstream performance.
- Perturbation-specific models ([[GEARS]], [[CPA]], [[scGen]]) are supervised rather than pretrained; see [[model type comparison]].

## Related
- [[input format comparison]] · [[architecture comparison]] · [[training objective comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #dataset #needs-verification
