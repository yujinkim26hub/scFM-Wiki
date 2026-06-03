---
title: <Model name>
aliases: [<model name>, <alt names>]
type: model
model_class: general-scfm | perturbation-specific | other
year: <YYYY>
tags: [scfm, model, needs-verification]
status: stub
updated: 2026-06-03
---

# <Model name>

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** State clearly what goes in, how it is represented, what comes out, and what the output may/may not be interpreted as biologically. Mark uncertain items `unclear` / `needs verification`. See [[AGENTS]] §5.

## 1. Overview
<One paragraph: what it is, who made it, what it is for. General scFM vs perturbation-specific.>

## 2. Original paper
<[[firstauthor-year-slug|Author Year]] — title, venue. Link to summary.>

## 3. Model type
<Pretrained foundation model / supervised perturbation model / generative model. [[single-cell foundation model]] or other.>

## Input

### 4. Input format
<scRNA-seq / snRNA-seq / scATAC-seq / multi-omics; counts vs normalized; #genes considered.>

### 5. Tokenization or encoding strategy
<Gene identity tokens / [[rank-based encoding]] / binned [[expression value encoding]] / raw value / [[condition token]] / metadata. Be exact.>

### 6. Pretraining data
<Corpus, #cells, source atlases. State if perturbation data were included, or n/a for non-pretrained models.>

## Processing / Architecture

### 7. Architecture
<Transformer encoder/decoder, Mamba/SSM, GNN, VAE… depth, params.>

### 8. Training objective
<Masked gene/value prediction, autoregressive, contrastive, reconstruction, etc.>

### 9. Interpretability
<Attention analysis, in silico perturbation, gene-network readouts — as reported.>

## Output

### 10. Model output
<Gene embeddings / [[cell embedding]] / predicted expression / class label / perturbation response. Which one(s)?>

### 11. Output interpretation
<What the output can and cannot be read as biologically. Embedding shift ≠ transcriptome prediction.>

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction. Do not overclaim.

### 12. Supported tasks
<Cell type annotation, integration, GRN inference, perturbation prediction…>

### 13. Zero-shot capability
<What works with frozen weights / embeddings. [[zero-shot prediction]].>

### 14. Fine-tuning capability
<What requires [[fine-tuning]]; typical heads.>

### 15. Perturbation capability
<Embedding shift vs classifier shift vs transcriptome-level prediction. Were perturbation data used for pretrain/fine-tune/eval/not used? [[in silico perturbation]] / [[perturbation prediction]].>

### 16. Batch correction or integration capability
<[[batch correction]] / [[data integration]] — reported behavior.>

## Evaluation

### 17. Benchmark and validation
<Benchmarks + metrics reported. Link [[Benchmarks]] pages.>

### 18. Disease or biological validation
<Disease/biology validation shown, if any. Neuro relevance if applicable. Don't overreach.>

## Practical use

### 19. Strengths
<Evidence-based strengths.>

### 20. Limitations
<Evidence-based limitations / open issues.>

### 21. Best use cases
<Where it is appropriate to apply.>

## Wiki links

### 22. Related models
<[[scGPT]], [[Geneformer]], …>

### 23. Related papers
<summary links>

### 24. Tags
#scfm #model <…>
