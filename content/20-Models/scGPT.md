---
title: scGPT
aliases: [scGPT]
type: model
model_class: general-scfm
year: 2024
tags: [scfm, model, transformer, perturbation, needs-verification]
status: stub
updated: 2026-06-03
---

# scGPT

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
scGPT is a general [[single-cell foundation model]] introduced by Cui et al. (Nature Methods, 2024). It is a generative transformer with specialized attention masking, pretrained on large single-cell corpora and adaptable to multiple downstream tasks including annotation, integration, GRN inference, and perturbation prediction.

## 2. Original paper
[[cui-2024-scgpt|Cui et al. 2024]] — "scGPT: toward building a foundation model for single-cell multi-omics using generative AI", Nature Methods 2024. Summary: to be ingested.

## 3. Model type
Pretrained generative [[single-cell foundation model]] (transformer). Can be fine-tuned for supervised tasks, including transcriptome-level [[perturbation prediction]].

## Input

### 4. Input format
scRNA-seq and multi-omic single-cell data; expression values are binned. Number of genes considered per cell needs verification.

### 5. Tokenization or encoding strategy
Gene identity tokens + binned [[expression value encoding|expression-value tokens]] + [[condition token]]s. Expression is discretized into bins rather than kept continuous; condition tokens encode metadata/experimental context (e.g. batch, perturbation condition).

### 6. Pretraining data
~33M cells from CELLxGENE (exact count needs verification). Source atlases via the CELLxGENE collection (specifics need verification). Perturbation data: not used for pretraining in the base model (needs verification); perturbation data are used for fine-tuning the perturbation-prediction task.

## Processing / Architecture

### 7. Architecture
Transformer with specialized attention masking adapted for generative single-cell modeling. Depth, hidden size, and parameter count need verification.

### 8. Training objective
Generative / masked prediction of gene expression (predicting expression values for masked genes in a generative formulation). Exact objective details need verification.

### 9. Interpretability
GRN inference from attention/embedding structure; gene-program and [[gene regulatory network]] readouts as reported. Specifics need verification.

## Output

### 10. Model output
[[gene embedding]]s and [[cell embedding]]s; can generate / predict gene expression values. With a fine-tuned head, outputs class labels or post-perturbation expression.

### 11. Output interpretation
For the perturbation task, fine-tuned scGPT predicts **post-perturbation gene expression** — a transcriptome-level prediction for genetic perturbations (as reported). Embeddings used for integration/annotation are representations, not expression predictions. Distinguish embedding-level outputs from the generative expression output.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction.

### 12. Supported tasks
[[cell type annotation]], batch integration / [[data integration]], multi-omic integration, [[gene regulatory network|GRN]] inference, and [[perturbation prediction]].

### 13. Zero-shot capability
Frozen embeddings can be used [[zero-shot prediction|zero-shot]], but independent benchmarks have questioned scGPT's zero-shot performance — some report that frozen scGPT embeddings underperform simpler baselines on certain tasks (as reported; needs verification). Treat zero-shot claims cautiously.

### 14. Fine-tuning capability
Strong reliance on [[fine-tuning]] with task-specific heads for annotation, integration, and perturbation prediction. Batch integration / data integration are reported in the fine-tuned setting.

### 15. Perturbation capability
[[perturbation prediction]] is performed by **fine-tuning on Perturb-seq data** to predict **post-perturbation expression** (transcriptome-level prediction for genetic perturbations). This is supervised use of perturbation data (fine-tuning), distinct from frozen-embedding analysis. Perturbation data use: fine-tuning + evaluation.

### 16. Batch correction or integration capability
[[batch correction]] / [[data integration]] reported, primarily in the fine-tuned setting, leveraging [[condition token]]s for batch/context (as reported).

## Evaluation

### 17. Benchmark and validation
The authors report results across annotation, integration, multi-omic, GRN, and perturbation tasks (specific datasets/metrics need verification). Independent reanalyses have scrutinized zero-shot embedding quality (needs verification). Link [[Benchmarks]] pages when ingested.

### 18. Disease or biological validation
Biological/disease validation specifics need verification. No clinical conclusions beyond the paper.

## Practical use

### 19. Strengths
Versatile multi-task foundation model; supports multi-omic input and condition tokens; fine-tuned transcriptome-level perturbation prediction.

### 20. Limitations
Reported zero-shot/frozen-embedding performance is contested by independent benchmarks (needs verification). Strong dependence on fine-tuning. Exact pretraining size and architecture details need verification.

### 21. Best use cases
Fine-tuned multi-task workflows: annotation, integration, GRN inference, and genetic perturbation-response prediction where labeled/perturbation data are available.

## Wiki links

### 22. Related models
[[Geneformer]], [[scFoundation]], [[scBERT]], [[scMamba]], [[CellPLM]]

### 23. Related papers
[[cui-2024-scgpt|Cui et al. 2024]] (summary: to be ingested)

### 24. Tags
#scfm #model #transformer #perturbation #data-integration #needs-verification
