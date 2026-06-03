---
title: model comparison overview
aliases: [model comparison overview]
type: comparison
criterion: overview
tags: [comparison, scfm, needs-verification]
status: stub
updated: 2026-06-03
---

# model comparison overview

> Master summary table across tracked models. One row per model; one column per high-level criterion. This is a navigational overview, **not** a ranking. Do **not** declare a winner. Every cell is a compact claim; deeper criteria live on the dedicated comparison pages linked below. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
A single-glance summary of model **class**, **year/venue**, **input encoding**, **output type**, **perturbation style**, and **zero-shot** status. Per-cell detail and evidence are deferred to the per-criterion pages; treat this table as an index, not a source. All entries below are marked "needs verification" until primary summaries are ingested.

## Summary table

| Model | Class | Year / venue | Input encoding | Output type | Perturbation style | Zero-shot |
|---|---|---|---|---|---|---|
| [[Geneformer]] | general scFM | 2023, Nature | rank-based gene encoding (no value tokens) | gene + cell embeddings | in-silico perturbation = embedding / cell-state shift | embeddings yes; classification needs fine-tuning |
| [[scGPT]] | general scFM | 2024, Nat Methods | gene tokens + binned expression + condition tokens | embeddings + expression generation | fine-tuned on Perturb-seq → transcriptome-level prediction | contested |
| [[scFoundation]] | general scFM | 2024, Nat Methods | raw continuous expression + read-depth (T/S) tokens | cell / gene embeddings | via pairing with [[GEARS]] (not itself) | needs verification |
| [[scBERT]] | general scFM | 2022, Nat Mach Intell | gene2vec + binned expression | class label (cell type) | none native | needs verification |
| [[scMamba]] | general scFM (SSM) | ~2024, needs verification | needs verification | needs verification | needs verification | needs verification |
| [[CellPLM]] | general scFM | 2024, ICLR | cells as tokens; inter-cell + spatial | cell embeddings | needs verification | needs verification |
| [[scPRINT]] | general scFM | ~2024, venue needs verification | needs verification | cell embeddings + GRN / gene-gene estimates | needs verification | needs verification |
| [[UCE]] | general scFM | 2023, bioRxiv | genes via protein-LM (ESM2) embeddings | cell embedding only | not for transcriptome-level perturbation | yes (vocabulary-free, no fine-tuning) |
| [[GeneCompass]] | general scFM | 2024, venue needs verification | knowledge-informed priors (GRN/promoter/family/co-expr) | gene + cell embeddings | needs verification | needs verification |
| [[GEARS]] | perturbation-specific | 2023, Nat Biotech | GNN over co-expression + GO graph | predicted post-perturbation expression | supervised transcriptome-level prediction (incl. unseen / combinatorial) | n/a (requires perturbation data) |
| [[CPA]] | perturbation-specific | 2023, Mol Syst Biol | disentangled additive latent (perturbation/dose/covariate) | predicted expression | supervised; predicts unseen combos | n/a (requires perturbation data) |
| [[scGen]] | perturbation-specific | 2019, Nat Methods | VAE latent + vector arithmetic | predicted expression response | supervised; generalizes response to unobserved cell types | n/a (not a foundation model) |

## Notes
- General scFMs (rows 1–9) are pretrained on large unlabeled atlases; perturbation-specific models (rows 10–12) are supervised on perturbation data and are not foundation models in the same sense. See [[model type comparison]].
- "Embedding shift" (e.g. [[Geneformer]] in-silico perturbation) and "transcriptome-level prediction" (e.g. [[GEARS]]) are different claims; see [[output interpretation comparison]] and [[perturbation capability comparison]].
- Every cell is "needs verification" pending ingestion of primary summaries.

## Related
- [[model type comparison]] · [[input format comparison]] · [[tokenization or encoding strategy comparison]] · [[pretraining data comparison]] · [[architecture comparison]] · [[training objective comparison]] · [[model output comparison]] · [[output interpretation comparison]] · [[supported tasks comparison]] · [[zero-shot capability comparison]] · [[fine-tuning capability comparison]] · [[perturbation capability comparison]] · [[batch correction or integration capability comparison]] · [[benchmark and validation comparison]] · [[disease or biological validation comparison]] · [[strengths and limitations comparison]] · [[best use cases comparison]]

## Tags
#comparison #scfm #needs-verification
