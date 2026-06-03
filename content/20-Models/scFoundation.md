---
title: scFoundation
aliases: [scFoundation, xTrimoGene]
type: model
model_class: general-scfm
year: 2024
tags: [scfm, model, transformer, perturbation, needs-verification]
status: stub
updated: 2026-06-03
---

# scFoundation

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
scFoundation is a general [[single-cell foundation model]] introduced by Hao et al. (Nature Methods, 2024). It is a large (~100M parameter) model built on the "xTrimoGene" asymmetric encoder-decoder transformer, designed to handle raw continuous expression and varying sequencing depth, and to provide embeddings for downstream single-cell tasks.

## 2. Original paper
[[hao-2024-scfoundation|Hao et al. 2024]] — "Large-scale foundation model on single-cell transcriptomics" (scFoundation / xTrimoGene), Nature Methods 2024. Summary: to be ingested.

## 3. Model type
Pretrained [[single-cell foundation model]] (asymmetric encoder-decoder transformer). Provides embeddings; transcriptome-level perturbation prediction is achieved by pairing with a downstream model (GEARS), not by scFoundation alone.

## Input

### 4. Input format
scRNA-seq single-cell transcriptomes using raw / continuous expression values (not binned). Read depth varies across cells and is handled explicitly. Number of genes considered needs verification.

### 5. Tokenization or encoding strategy
Raw / continuous [[expression value encoding|expression values]] (not binned), with read-depth awareness via total-count tokens (referred to as T/S tokens) so the model is aware of, and robust to, differing sequencing depth between input and target. Not [[rank-based encoding]]; not binned tokens.

### 6. Pretraining data
~50M single cells (needs verification). Source atlases / corpus composition need verification. Perturbation data: not used for pretraining (needs verification).

## Processing / Architecture

### 7. Architecture
"xTrimoGene" asymmetric encoder-decoder transformer, ~100M parameters. Asymmetry (larger encoder, lighter decoder) and exact layer/hidden dimensions need verification.

### 8. Training objective
Self-supervised reconstruction/prediction of expression values, with a read-depth-aware formulation (predicting higher-depth expression from lower-depth input). Exact objective details need verification.

### 9. Interpretability
Gene-context embeddings used for downstream analyses including [[gene regulatory network|GRN]] tasks; interpretability specifics need verification.

## Output

### 10. Model output
[[cell embedding]]s and contextual [[gene embedding]]s. These embeddings feed downstream task models.

### 11. Output interpretation
scFoundation itself produces **embeddings**, not transcriptome-level perturbation predictions. When transcriptome-level genetic [[perturbation prediction]] is reported, it comes from feeding scFoundation embeddings into the downstream **GEARS** pipeline. Embedding outputs should not be read directly as predicted post-perturbation expression.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction.

### 12. Supported tasks
[[cell type annotation]], drug-response prediction, [[gene regulatory network|GRN]] analysis, and [[perturbation prediction]] (via the GEARS pipeline).

### 13. Zero-shot capability
Frozen scFoundation embeddings are usable [[zero-shot prediction|zero-shot]] as inputs to downstream analyses (extent and quality need verification).

### 14. Fine-tuning capability
Embeddings can be used with downstream task heads / models; [[fine-tuning]] specifics per task need verification.

### 15. Perturbation capability
Transcriptome-level genetic [[perturbation prediction]] is achieved by **combining scFoundation embeddings with GEARS** (a separate perturbation model). scFoundation supplies representations; GEARS supplies the perturbation-response prediction. Perturbation data are used in the downstream (GEARS) stage, not in scFoundation pretraining (needs verification).

### 16. Batch correction or integration capability
[[batch correction]] / [[data integration]] behavior needs verification; read-depth awareness may aid robustness across datasets (as reported; needs verification).

## Evaluation

### 17. Benchmark and validation
The authors report results on cell type annotation, drug-response, GRN, and perturbation tasks (specific datasets/metrics need verification). Link [[Benchmarks]] pages when ingested.

### 18. Disease or biological validation
Drug-response prediction is reported; specific disease/biological validation details need verification. No clinical conclusions beyond the paper.

## Practical use

### 19. Strengths
Raw continuous-value input with explicit read-depth handling; large scale (~100M params); embeddings transferable to multiple downstream tasks.

### 20. Limitations
Does not itself predict post-perturbation transcriptomes — relies on GEARS for that. Exact pretraining size, architecture details, and benchmark specifics need verification.

### 21. Best use cases
Embedding extraction for annotation, drug-response, and GRN tasks; as an embedding front-end to GEARS for genetic perturbation-response prediction.

## Wiki links

### 22. Related models
[[Geneformer]], [[scGPT]], [[scBERT]], [[scMamba]], [[CellPLM]]

### 23. Related papers
[[hao-2024-scfoundation|Hao et al. 2024]] (summary: to be ingested)

### 24. Tags
#scfm #model #transformer #perturbation #needs-verification
