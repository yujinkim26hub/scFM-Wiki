---
title: single-cell foundation model
aliases: [single-cell foundation model, single-cell foundation models, scFM, cell foundation model]
type: concept
tags: [concept, scfm, transformer]
status: stub
updated: 2026-06-03
---

# single-cell foundation model

## Definition
A single-cell foundation model (scFM) is a large neural network pretrained in a self-supervised manner on large collections of single-cell profiles (typically millions of cells from scRNA-seq atlases) to produce reusable [[gene embedding|gene]] and [[cell embedding|cell]] representations that can be transferred to many downstream tasks. The "foundation" framing borrows from NLP: pretrain once on broad unlabeled data, then adapt via [[zero-shot prediction|zero-shot]] use of frozen embeddings or via [[fine-tuning]] with a task head.

## Why it matters for scFMs
The central premise is [[transfer learning]]: representations learned from unlabeled atlases should generalize to tasks where labeled data is scarce (cell-type annotation, [[batch correction]], [[data integration]], [[gene regulatory network]] inference, [[in-silico perturbation]]). Whether scFMs actually deliver on this premise relative to simpler baselines is an active, contested question.

## How it works / key distinctions
- **General scFMs** are pretrained self-supervised on broad single-cell data: [[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[UCE]], [[CellPLM]], [[scPRINT]], [[GeneCompass]], [[scMamba]]. They differ in [[tokenization-strategy|tokenization]] (e.g. [[rank-based encoding]] vs [[expression value encoding]]) and architecture (BERT-style, GPT-style, state-space).
- **Perturbation-specific models** ([[GEARS]], [[CPA]], [[scGen]]) are *not* foundation models in the same sense: they are trained specifically to predict transcriptional responses to perturbation and are not broadly pretrained self-supervised. Keep them distinct (AGENTS.md §0.6).
- Capability classes must be kept separate: [[zero-shot prediction|zero-shot]] (frozen) vs [[fine-tuning]] vs supervised [[perturbation prediction]].

## Common pitfalls / what it is not
- An scFM is not a [[virtual cell model]]; it is at most a building block toward one.
- Pretraining scale does not guarantee downstream superiority. Several independent benchmarks report that scFMs do not consistently beat simpler methods (e.g. highly-variable-gene + PCA, scVI) on integration or annotation in [[zero-shot prediction|zero-shot]] settings (needs verification of specifics).
- The field carries substantial hype; benchmark claims should be checked against independent, leakage-controlled evaluations.

## Models / methods that use it
- General scFMs: [[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[UCE]], [[CellPLM]], [[scPRINT]], [[GeneCompass]], [[scMamba]].
- Perturbation-specific (contrast): [[GEARS]], [[CPA]], [[scGen]].
- **Example (ingested):** [[rosen-2023-universal-cell-embeddings|UCE (Rosen 2023)]] — a **zero-shot, cross-species** scFM (ESM2 protein-embedding gene encoding; ~36M cells across 8 species; 33-layer/~650M transformer) that emits a universal [[cell embedding]].

## Related concepts
[[gene embedding]], [[cell embedding]], [[transfer learning]], [[zero-shot prediction]], [[fine-tuning]], [[tokenization-strategy|tokenization strategy]], [[virtual cell model]]

## Tags
#concept #scfm #transformer #needs-verification
