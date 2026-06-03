---
title: scBERT
aliases: [scBERT]
type: model
model_class: general-scfm
year: 2022
tags: [scfm, model, transformer, needs-verification]
status: stub
updated: 2026-06-03
---

# scBERT

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
scBERT is a general [[single-cell foundation model]] introduced by Yang et al. (Nature Machine Intelligence, 2022). It is a BERT-based model that uses Performer (efficient/linear attention) to scale to the full gene panel, and is primarily applied to cell type annotation via fine-tuning. It predates and is narrower in scope than later scFMs.

## 2. Original paper
[[yang-2022-scbert|Yang et al. 2022]] — "scBERT as a large-scale pretrained deep language model for cell type annotation of single-cell RNA-seq data", Nature Machine Intelligence 2022. Summary: to be ingested.

## 3. Model type
Pretrained [[single-cell foundation model]] (BERT-based, Performer attention). Fine-tuned for supervised cell type annotation. Not a perturbation model.

## Input

### 4. Input format
scRNA-seq single-cell transcriptomes spanning a large gene panel (~16k–20k genes; exact count needs verification). Performer attention enables scaling to this many genes.

### 5. Tokenization or encoding strategy
Per gene, a gene2vec gene-identity embedding is combined with a binned [[expression value encoding|expression embedding]]. Gene identity comes from gene2vec; expression is discretized into bins. Not [[rank-based encoding]]; no [[condition token]] in the base model.

### 6. Pretraining data
PanglaoDB (~1M+ cells; exact count needs verification). Perturbation data: not used.

## Processing / Architecture

### 7. Architecture
BERT-style transformer using Performer (linear/efficient attention) to handle long gene sequences. Depth, hidden size, and parameter count need verification.

### 8. Training objective
Self-supervised masked prediction (BERT-style masking over genes/expression). Exact objective details need verification.

### 9. Interpretability
Attention-based gene-importance analysis reported for annotation; specifics need verification.

## Output

### 10. Model output
[[cell embedding]] / [[gene embedding]] representations; with a fine-tuned classification head, outputs cell type labels.

### 11. Output interpretation
Primary output is a representation feeding a classifier; the annotation output is a **class label / classifier score**, not a transcriptome-level prediction. No perturbation-response output.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction.

### 12. Supported tasks
[[cell type annotation]] (primary, fine-tuned). Broader multi-task capabilities of later scFMs are not the focus here.

### 13. Zero-shot capability
[[zero-shot prediction|Zero-shot]] use of frozen embeddings is not the model's emphasized use; performance needs verification.

### 14. Fine-tuning capability
[[fine-tuning]] with a classification head for cell type annotation is the primary supported workflow (as reported).

### 15. Perturbation capability
No native [[perturbation prediction]]. Perturbation data: not used (pretraining, fine-tuning, or evaluation).

### 16. Batch correction or integration capability
[[batch correction]] / [[data integration]] is not a primary advertised capability; reported behavior needs verification.

## Evaluation

### 17. Benchmark and validation
The authors report cell type annotation benchmarks against contemporary methods (specific datasets/metrics need verification). Link [[Benchmarks]] pages when ingested.

### 18. Disease or biological validation
Disease/biological validation specifics need verification. No clinical conclusions beyond the paper.

## Practical use

### 19. Strengths
Early scFM; Performer attention scales to the full gene panel; combines gene2vec identity with binned expression; effective at annotation (as reported).

### 20. Limitations
Narrower scope than later scFMs (annotation-focused, no native perturbation prediction). Exact gene-panel size, pretraining count, and architecture details need verification.

### 21. Best use cases
Cell type annotation of scRNA-seq via fine-tuning.

## Wiki links

### 22. Related models
[[Geneformer]], [[scGPT]], [[scFoundation]], [[scMamba]], [[CellPLM]]

### 23. Related papers
[[yang-2022-scbert|Yang et al. 2022]] (summary: to be ingested)

### 24. Tags
#scfm #model #transformer #cell-type-annotation #needs-verification
