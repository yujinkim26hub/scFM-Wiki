---
title: GEARS
aliases: [GEARS]
type: model
model_class: perturbation-specific
year: 2023
tags: [scfm, model, perturbation, gnn, needs-verification]
status: stub
updated: 2026-06-03
---

# GEARS

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
GEARS is a **perturbation-specific model — NOT a pretrained [[single-cell foundation model]]**. Introduced by Roohani et al., Nature Biotechnology 2023, it is a graph neural network (GNN) that combines a **gene co-expression graph** with a **Gene-Ontology-derived knowledge graph** to **predict post-perturbation gene expression at the transcriptome level** for genetic perturbations — including **unseen single and combinatorial perturbations**. It is trained in a **supervised** fashion on [[Perturb-seq]] data and requires perturbation data for training.

## 2. Original paper
Roohani et al., 2023 — GEARS, Nature Biotechnology. summary: to be ingested.

## 3. Model type
**Supervised perturbation-prediction model** (graph neural network). Perturbation-specific, not a general scFM. Predicts transcriptome-level expression responses.

## Input

### 4. Input format
scRNA-seq expression profiles plus a specified genetic perturbation (gene(s) knocked out / activated). Trained on [[Perturb-seq]] data. Counts vs normalized: needs verification.

### 5. Tokenization or encoding strategy
No language-model tokenization. Genes and perturbations are represented as nodes in two graphs: (1) a **gene co-expression graph** and (2) a **Gene-Ontology (GO) knowledge graph** relating perturbations. Perturbations are encoded through their position/relations in these graphs, enabling generalization to **unseen** perturbations.

### 6. Pretraining data
**Not a pretrained foundation model.** Perturbation data are used for **supervised training**, not self-supervised pretraining. It is commonly **paired with scFM embeddings** (e.g. [[scFoundation]]) as input features (needs verification of exact coupling).

## Processing / Architecture

### 7. Architecture
Graph neural network operating over the gene co-expression graph and the GO-derived knowledge graph (depth / parameter count: needs verification).

### 8. Training objective
Supervised regression to the observed post-perturbation expression profile (exact loss formulation needs verification).

### 9. Interpretability
The GO knowledge graph provides structured relations between perturbations; this supports reasoning about combinatorial and unseen perturbations. Specific interpretability analyses: needs verification.

## Output

### 10. Model output
A **predicted post-perturbation gene expression profile** — a true **transcriptome-level** [[perturbation prediction]] (not merely an embedding shift or classifier score).

### 11. Output interpretation
The output is a quantitative predicted expression profile for a cell/population under a given genetic perturbation. It is a model prediction and should be validated; predictive accuracy varies by perturbation and especially for combinatorial/unseen cases.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction. Do not overclaim.

### 12. Supported tasks
Genetic [[perturbation prediction]] at transcriptome level, including unseen single perturbations and unseen combinatorial perturbations.

### 13. Zero-shot capability
Not zero-shot in the scFM sense (no frozen-embedding inference). It does generalize to **unseen perturbations** by leveraging the GO knowledge graph, but this requires a trained model.

### 14. Fine-tuning capability
Not applicable in the scFM fine-tuning sense; the model is trained (supervised) on perturbation data rather than fine-tuned from a self-supervised checkpoint.

### 15. Perturbation capability
**Core capability:** true transcriptome-level [[perturbation prediction]] for genetic perturbations. Perturbation data use: **training (supervised)**. Distinct from [[in silico perturbation]] via embedding shift in scFMs — GEARS predicts the actual expression response.

### 16. Batch correction or integration capability
Not a [[batch correction]] / [[data integration]] method; not applicable.

## Evaluation

### 17. Benchmark and validation
Evaluated on [[Perturb-seq]] perturbation datasets, including held-out single and combinatorial perturbations (exact datasets/metrics need verification). To be linked under [[Benchmarks]].

### 18. Disease or biological validation
Disease validation: needs verification. Focus is mechanistic/genetic perturbation response. Do not overreach.

## Practical use

### 19. Strengths
Predicts full expression responses to genetic perturbations; generalizes to unseen single and combinatorial perturbations via GO knowledge graph.

### 20. Limitations
Requires perturbation (Perturb-seq) data for training; accuracy varies for unseen/combinatorial perturbations; scope is genetic perturbations.

### 21. Best use cases
Prioritizing/predicting genetic perturbation outcomes (including combinations) when [[Perturb-seq]] training data are available; can be combined with scFM embeddings such as [[scFoundation]].

## Wiki links

### 22. Related models
[[CPA]], [[scGen]], [[scFoundation]], [[scGPT]], [[GeneCompass]]

### 23. Related papers
Roohani et al. 2023 (summary: to be ingested).

### 24. Tags
#scfm #model #perturbation #needs-verification
