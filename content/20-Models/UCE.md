---
title: UCE
aliases: [UCE, Universal Cell Embeddings, Universal Cell Embedding]
type: model
model_class: general-scfm
year: 2023
tags: [scfm, model, transformer, zero-shot, cross-species, needs-verification]
status: stub
updated: 2026-06-03
---

# UCE (Universal Cell Embeddings)

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
UCE ("Universal Cell Embeddings") is a general [[single-cell foundation model]] introduced by Rosen et al., 2023 (bioRxiv; venue/year need verification). Its distinctive idea is to represent each gene by its **protein-sequence embedding** from a protein language model (e.g. ESM2) rather than by a fixed gene-ID vocabulary. Because genes are grounded in protein sequence, UCE produces **cross-species, zero-shot universal [[cell embedding]]s** with no fine-tuning and no shared gene vocabulary across datasets or species.

## 2. Original paper
Rosen et al., 2023 — "Universal Cell Embeddings" (UCE), bioRxiv (venue/year need verification). summary: to be ingested.

## 3. Model type
Pretrained general [[single-cell foundation model]]; self-supervised transformer over genes/cells. Not a perturbation-specific model.

## Input

### 4. Input format
scRNA-seq expression. Counts vs normalized: needs verification. Number of genes considered per cell: needs verification.

### 5. Tokenization or encoding strategy
Genes are encoded via **protein language model embeddings** (e.g. ESM2) of the gene's protein sequence, rather than a fixed gene-identity token vocabulary. This sequence grounding is what enables a shared representation across species without a common gene vocabulary. Exact assembly of expression + protein embeddings into model input: needs verification.

### 6. Pretraining data
Pretrained self-supervised on tens of millions of cells across multiple species (exact #cells and #species need verification). No perturbation data used as a pretraining corpus (needs verification, but consistent with its embedding focus).

## Processing / Architecture

### 7. Architecture
Self-supervised transformer over genes/cells (depth / parameter count: needs verification).

### 8. Training objective
Self-supervised (objective formulation needs verification).

### 9. Interpretability
Cross-species comparability of embeddings is itself a useful analysis property; specific interpretability methods (attention, etc.): needs verification.

## Output

### 10. Model output
A **universal [[cell embedding]]** — a fixed-dimensional vector per cell, comparable across datasets and species.

### 11. Output interpretation
The output is a learned cell representation usable for annotation, integration, and atlas mapping. It is **not** a transcriptome-level expression prediction and is **not** designed for [[perturbation prediction]]. Distances/shifts in this embedding space are not expression predictions.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction. Do not overclaim.

### 12. Supported tasks
Cell type annotation, [[data integration]], and atlas mapping via the universal embedding; cross-species transfer.

### 13. Zero-shot capability
Central strength: [[zero-shot prediction]] use of frozen universal embeddings with **no fine-tuning** and no shared gene vocabulary, including across species.

### 14. Fine-tuning capability
Designed for zero-shot use; whether/how it is fine-tuned with task heads: needs verification.

### 15. Perturbation capability
Not designed for transcriptome-level [[perturbation prediction]]. Perturbation data use (pretrain / fine-tune / eval / not used): **not used** as a core purpose (needs verification). Any [[in silico perturbation]] via embedding shift would be an embedding-space operation, not a true expression prediction.

### 16. Batch correction or integration capability
The universal embedding supports cross-dataset / cross-species [[data integration]] and [[batch correction]]-style alignment; quantitative behavior: needs verification.

## Evaluation

### 17. Benchmark and validation
Benchmarks and metrics (annotation, integration, cross-species transfer): needs verification. To be linked under [[Benchmarks]].

### 18. Disease or biological validation
Disease / biological validation: needs verification. Do not overreach.

## Practical use

### 19. Strengths
Cross-species, vocabulary-free, zero-shot universal embeddings; novel protein-sequence grounding of genes.

### 20. Limitations
Embedding-only output (no expression prediction); quantitative specifics unverified here; depends on quality of the underlying protein language model embeddings.

### 21. Best use cases
Cross-species cell annotation, atlas mapping, and integration where a shared gene vocabulary is unavailable.

## Wiki links

### 22. Related models
[[Geneformer]], [[scGPT]], [[scFoundation]], [[GeneCompass]], [[scPRINT]], [[CellPLM]]

### 23. Related papers
Rosen et al. 2023 (summary: to be ingested).

### 24. Tags
#scfm #model #transformer #zero-shot #needs-verification
