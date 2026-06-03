---
title: GeneCompass
aliases: [GeneCompass]
type: model
model_class: general-scfm
year: 2024
tags: [scfm, model, transformer, cross-species, needs-verification]
status: stub
updated: 2026-06-03
---

# GeneCompass

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
GeneCompass is a general, **cross-species** (human + mouse) [[single-cell foundation model]] introduced by Yang et al., 2024 (Cell Research / bioRxiv — needs verification). Its distinctive feature is that it is **"knowledge-informed"**: it incorporates **prior biological knowledge** — gene regulatory networks, promoter information, gene family, and gene co-expression — into pretraining, alongside a large cross-species corpus.

## 2. Original paper
Yang et al., 2024 — GeneCompass (Cell Research / bioRxiv; venue needs verification). summary: to be ingested.

## 3. Model type
Pretrained general [[single-cell foundation model]]; transformer with knowledge priors. Not a perturbation-specific model.

## Input

### 4. Input format
scRNA-seq expression from human and mouse. Counts vs normalized: needs verification. Number of genes considered: needs verification.

### 5. Tokenization or encoding strategy
Encoding combines gene expression with injected **prior-knowledge features** (gene regulatory networks, promoter information, gene family, gene co-expression). Exact tokenization (gene identity tokens vs binned vs raw value, and how priors are fused): **needs verification**.

### 6. Pretraining data
Large cross-species corpus of ~120M cells across human + mouse (exact #cells / composition need verification). Whether perturbation data were included in pretraining: needs verification (assume not a core corpus unless confirmed).

## Processing / Architecture

### 7. Architecture
Transformer (depth / parameter count: needs verification), with mechanisms to incorporate prior-knowledge inputs.

### 8. Training objective
Self-supervised pretraining informed by biological priors (exact objective formulation needs verification).

### 9. Interpretability
Knowledge priors (GRN, promoter, gene family, co-expression) may aid biological interpretation; specific interpretability analyses: needs verification.

## Output

### 10. Model output
Gene and cell embeddings (a [[gene embedding]] and [[cell embedding]]).

### 11. Output interpretation
Outputs are learned embeddings, not transcriptome-level expression predictions. Reported downstream uses (e.g. GRN inference, drug response) are model outputs/analyses, not validated biology, and the specific task list needs verification.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction. Do not overclaim.

### 12. Supported tasks
Reported tasks include cell type annotation, [[gene regulatory network]] inference, drug-response prediction, and perturbation-related analyses (**verify** — exact task set and how each is evaluated need verification).

### 13. Zero-shot capability
Frozen-embedding ([[zero-shot prediction]]) use: capability and scope need verification.

### 14. Fine-tuning capability
[[fine-tuning]] with task heads for annotation / GRN / drug response is plausible; typical heads need verification.

### 15. Perturbation capability
"Perturbation-related analyses" are reported but the **type** of output (embedding shift vs classifier shift vs true transcriptome-level [[perturbation prediction]]) needs verification — do not assume true expression prediction. Perturbation data use (pretrain / fine-tune / eval / not used): needs verification.

### 16. Batch correction or integration capability
[[data integration]] / [[batch correction]], especially cross-species: reported behavior needs verification.

## Evaluation

### 17. Benchmark and validation
Benchmarks and metrics across the reported tasks: needs verification. To be linked under [[Benchmarks]].

### 18. Disease or biological validation
Disease / biological validation (e.g. via drug response): needs verification. Do not overreach.

## Practical use

### 19. Strengths
Cross-species (human + mouse) coverage and explicit injection of biological prior knowledge into pretraining.

### 20. Limitations
Many architectural and quantitative specifics unverified here; the precise nature of "perturbation-related" outputs is unconfirmed.

### 21. Best use cases
Cross-species single-cell analysis and tasks that may benefit from injected biological priors (annotation, GRN inference), pending verification of task-specific claims.

## Wiki links

### 22. Related models
[[UCE]], [[scPRINT]], [[Geneformer]], [[scGPT]], [[scFoundation]]

### 23. Related papers
Yang et al. 2024 (summary: to be ingested).

### 24. Tags
#scfm #model #transformer #needs-verification
