---
title: scPRINT
aliases: [scPRINT]
type: model
model_class: general-scfm
year: 2024
tags: [scfm, model, transformer, gene-regulatory-network, needs-verification]
status: stub
updated: 2026-06-03
---

# scPRINT

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
scPRINT is a general [[single-cell foundation model]] (general scFM) whose distinctive focus is **[[gene regulatory network]] (GRN) inference**. It was introduced by Kalfon et al. (~2024–2025; venue needs verification — bioRxiv / Nature Communications). It is trained with a **multi-task** objective (e.g. denoising, label / cell-property prediction, and gene-network inference) and is intended to produce both [[cell embedding]]s and estimates of gene–gene interactions / regulatory relationships. Its GRN-inference orientation distinguishes it from scFMs aimed primarily at annotation or integration (e.g. [[Geneformer]], [[scGPT]]).

## 2. Original paper
Kalfon et al., ~2024 — scPRINT (venue needs verification: bioRxiv / Nature Communications). summary: to be ingested.

## 3. Model type
Pretrained general [[single-cell foundation model]] with a multi-task pretraining setup that includes gene-network inference. Not a perturbation-specific model.

## Input

### 4. Input format
scRNA-seq expression (counts vs normalized: needs verification); number of genes considered: needs verification.

### 5. Tokenization or encoding strategy
Input representation / encoding (gene identity tokens vs binned vs raw value): **needs verification**. Do not assume; the precise encoding has not been confirmed here.

### 6. Pretraining data
Corpus size, #cells, and source atlases: **needs verification**. Whether perturbation data were included in pretraining: needs verification (likely not a primary corpus, but unconfirmed).

## Processing / Architecture

### 7. Architecture
Transformer-based (depth / parameter count: needs verification). Designed so that gene relationships / a [[gene regulatory network]] can be read out (often from attention or learned gene-gene relationships — needs verification).

### 8. Training objective
Multi-task pretraining: denoising, label / cell-property prediction, and gene regulatory network inference (exact objective formulations need verification).

### 9. Interpretability
Explicit GRN read-out is a central design goal — gene–gene interaction estimates may be derived from attention or learned gene relationships (mechanism needs verification). This is more interpretability-forward than scFMs that only emit embeddings.

## Output

### 10. Model output
Two main outputs: (a) a [[cell embedding]], and (b) gene–gene interaction / [[gene regulatory network]] estimates.

### 11. Output interpretation
The GRN output is an **inferred** network from model-internal relationships, not a validated causal regulatory map; treat edges as hypotheses pending experimental validation. The cell embedding is a learned latent representation, not a transcriptome-level prediction. scPRINT is not designed to output true post-perturbation expression profiles.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction. Do not overclaim.

### 12. Supported tasks
[[gene regulatory network]] inference (primary), cell-property / label prediction, denoising, and [[cell embedding]] generation. Other downstream tasks: needs verification.

### 13. Zero-shot capability
Frozen-embedding ([[zero-shot prediction]]) use for embeddings and GRN read-out is plausible given the multi-task pretraining, but the exact zero-shot claims need verification.

### 14. Fine-tuning capability
[[fine-tuning]] with task heads: capability and typical heads need verification.

### 15. Perturbation capability
No claim of true transcriptome-level [[perturbation prediction]]. Whether [[in silico perturbation]] is supported via the inferred network: needs verification. Perturbation data use (pretrain / fine-tune / eval / not used): needs verification — assume **not a core use** unless confirmed.

### 16. Batch correction or integration capability
[[batch correction]] / [[data integration]] behavior: needs verification.

## Evaluation

### 17. Benchmark and validation
Benchmarks and metrics (especially GRN-inference benchmarks): needs verification. To be linked under [[Benchmarks]] once ingested.

### 18. Disease or biological validation
Disease / biological validation: needs verification. Do not overreach.

## Practical use

### 19. Strengths
Distinctive GRN-inference focus; multi-task pretraining yielding embeddings plus network estimates (claims pending verification).

### 20. Limitations
Most architectural and quantitative specifics are unverified here. Inferred GRNs require independent validation.

### 21. Best use cases
Exploratory [[gene regulatory network]] inference and cell representation from scRNA-seq, with downstream experimental validation of network hypotheses.

## Wiki links

### 22. Related models
[[Geneformer]], [[scGPT]], [[scFoundation]], [[UCE]], [[GeneCompass]]

### 23. Related papers
Kalfon et al. ~2024 (summary: to be ingested).

### 24. Tags
#scfm #model #transformer #gene-regulatory-network #needs-verification
