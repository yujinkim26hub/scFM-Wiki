---
title: CellPLM
aliases: [CellPLM, Cell Pre-trained Language Model]
type: model
model_class: general-scfm
year: 2024
tags: [scfm, model, transformer, spatial, needs-verification]
status: stub
updated: 2026-06-03
---

# CellPLM

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
CellPLM ("Cell Pre-trained Language Model") is a general [[single-cell foundation model]] introduced by Wen et al. (ICLR 2024). Its distinctive feature is that it treats **cells as tokens** and explicitly models relationships **between** cells (cell-cell, including spatial transcriptomics), using a transformer encoder with a Gaussian-mixture latent prior.

## 2. Original paper
[[wen-2024-cellplm|Wen et al. 2024]] — "CellPLM: Pre-training of Cell Language Model Beyond Single Cells", ICLR 2024. Summary: to be ingested.

## 3. Model type
Pretrained [[single-cell foundation model]] (transformer encoder with a Gaussian-mixture latent prior). Models inter-cell relationships rather than only within-cell gene structure.

## Input

### 4. Input format
Single-cell (and spatial) gene expression. Each cell is treated as a token, and sets of cells (including spatial neighborhoods) are modeled jointly. Exact #genes and preprocessing need verification.

### 5. Tokenization or encoding strategy
Cells as tokens: gene-expression vectors per cell are encoded into cell-level tokens, and the model attends across cells to capture cell-cell relationships (incl. spatial context). This differs from gene-as-token scFMs. Exact per-cell encoding details need verification; not [[rank-based encoding]].

### 6. Pretraining data
Pretraining corpus and #cells need verification; reported to include spatial transcriptomics data alongside scRNA-seq (needs verification). Perturbation data use: needs verification.

## Processing / Architecture

### 7. Architecture
Transformer encoder operating over cells as tokens, with a Gaussian-mixture latent prior. Depth, dimensions, and parameter count need verification.

### 8. Training objective
Self-supervised pretraining (e.g. masked reconstruction over cells/genes) combined with the latent-prior objective; exact formulation needs verification.

### 9. Interpretability
Interpretability via the latent structure / cell-cell relationships as reported; specifics need verification.

## Output

### 10. Model output
[[cell embedding]]s that incorporate inter-cell context; can support imputation and downstream task heads.

### 11. Output interpretation
Outputs are cell-level representations that encode relationships between cells (including spatial neighbors). Imputation outputs reconstruct expression; representation outputs are embeddings, not perturbation predictions. Distinguish per task; specifics need verification.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction.

### 12. Supported tasks
Reported to support imputation, [[cell type annotation]], spatial tasks, and perturbation-related tasks (verify exactly which and in what mode). The leveraging of inter-cell / spatial relationships is the distinctive capability.

### 13. Zero-shot capability
[[zero-shot prediction|Zero-shot]] use of frozen cell embeddings needs verification.

### 14. Fine-tuning capability
[[fine-tuning]] with task heads for annotation/imputation/spatial tasks; specifics need verification.

### 15. Perturbation capability
Perturbation-related tasks are reported, but whether this is embedding shift, classifier shift, or transcriptome-level [[perturbation prediction]] — and whether perturbation data were used for fine-tuning vs evaluation — needs verification.

### 16. Batch correction or integration capability
[[batch correction]] / [[data integration]] capability needs verification.

## Evaluation

### 17. Benchmark and validation
The authors report results on imputation, annotation, and spatial tasks (specific datasets/metrics need verification). Link [[Benchmarks]] pages when ingested.

### 18. Disease or biological validation
Disease/biological validation specifics need verification. No clinical conclusions beyond the paper.

## Practical use

### 19. Strengths
Distinctive modeling of cell-cell relationships, including spatial transcriptomics; cells-as-tokens design; Gaussian-mixture latent prior for structured embeddings (as reported).

### 20. Limitations
Cells-as-tokens design differs from gene-token scFMs and may suit different tasks. Exact pretraining data, objective, and benchmark specifics need verification.

### 21. Best use cases
Tasks where inter-cell or spatial context matters: spatial transcriptomics analysis, imputation, and annotation leveraging neighborhood structure.

## Wiki links

### 22. Related models
[[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[scMamba]]

### 23. Related papers
[[wen-2024-cellplm|Wen et al. 2024]] (summary: to be ingested)

### 24. Tags
#scfm #model #transformer #spatial #needs-verification
