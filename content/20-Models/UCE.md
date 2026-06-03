---
title: UCE
aliases: [UCE, Universal Cell Embeddings, Universal Cell Embedding]
type: model
model_class: general-scfm
year: 2023
tags: [scfm, model, transformer, zero-shot, cross-species]
status: draft
updated: 2026-06-03
---

# UCE (Universal Cell Embeddings)

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5. Primary source: [[rosen-2023-universal-cell-embeddings|Rosen 2023]].

## 1. Overview
UCE ("Universal Cell Embeddings") is a general [[single-cell foundation model]] introduced by [[rosen-2023-universal-cell-embeddings|Rosen et al., 2023 (bioRxiv)]]. Its distinctive idea is to represent each gene by the **protein-language-model (ESM2) embedding of its protein product** rather than by a fixed gene-ID vocabulary. Because genes are grounded in protein sequence, UCE produces **cross-species, zero-shot universal [[cell embedding]]s** — no fine-tuning and no shared gene vocabulary across datasets or species.

## 2. Original paper
[[rosen-2023-universal-cell-embeddings|Rosen et al. 2023]] — "Universal Cell Embeddings: A Foundation Model for Cell Biology", bioRxiv, DOI [10.1101/2023.11.28.568918](https://doi.org/10.1101/2023.11.28.568918). Code: [snap-stanford/UCE](https://github.com/snap-stanford/UCE). Summary: [[rosen-2023-universal-cell-embeddings]].

## 3. Model type
Pretrained general [[single-cell foundation model]]; self-supervised transformer. **Not** a perturbation-specific model.

## Input

### 4. Input format
scRNA-seq / snRNA-seq single-cell expression (counts), across multiple species. No cell-type labels needed at inference.

### 5. Tokenization or encoding strategy
Genes are **not** fixed identity tokens. Each gene is encoded by the **ESM2 protein-language-model embedding** of its protein product, which is what enables a shared representation across species without a common gene vocabulary. A cell is turned into a **"cell sentence"**: a sample of its expressed genes, drawn **with replacement, weighted by expression** — so expression magnitude enters via sampling frequency, not binned/raw value tokens. Contrast [[rank-based encoding]] (Geneformer) and binned [[expression value encoding]] (scGPT/scBERT). See [[tokenization strategy]]. (Genomic/positional encoding details: `needs verification`.)

### 6. Pretraining data
Self-supervised pretraining on **~36 million single-cell transcriptomes across 8 species** (human, mouse, zebrafish, mouse lemur, crab-eating macaque, rhesus macaque, tropical clawed frog, pig) and dozens of tissues (the Integrated Mega-scale Atlas, IMA). Exact dataset count: `needs verification`. **Perturbation data: not used.**

## Processing / Architecture

### 7. Architecture
Transformer encoder; the released main model is a **33-layer transformer with ~650 million parameters** (a smaller 4-layer model is also released).

### 8. Training objective
Self-supervised **masked binary prediction**: the model distinguishes genes that were truly expressed in a cell from genes with zero expression. No labels/annotations required.

### 9. Interpretability
The cross-species comparability of the embedding space is itself the main analysis property (coherent, label-free organization of cell types/lineages). No attention-based mechanistic interpretability is claimed; specifics `needs verification`.

## Output

### 10. Model output
A **universal [[cell embedding]]** — a fixed-dimensional vector per cell (commonly cited as 1280-d; exact value `needs verification`), comparable across datasets and species.

### 11. Output interpretation
A learned cell representation for annotation, integration, and atlas mapping. It is **not** a transcriptome-level expression prediction and **not** a [[perturbation prediction]]. Distances/shifts in this space describe representational similarity, **not** predicted gene expression.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction. Do not overclaim.

### 12. Supported tasks
Zero-shot [[cell embedding]] generation; cell-type organization/annotation via embedding structure or label transfer; cross-species and cross-dataset [[data integration]] / [[batch correction]]; mapping new datasets onto the IMA (atlas mapping).

### 13. Zero-shot capability
Central strength: [[zero-shot prediction]] use of frozen universal embeddings with **no fine-tuning** and no shared gene vocabulary, including for **previously unseen species**.

### 14. Fine-tuning capability
By design, **none** — the authors state UCE "is not intended to be finetuned." Use is zero-shot. See [[fine-tuning]].

### 15. Perturbation capability
**Not designed for perturbation.** No [[in silico perturbation]] or [[perturbation prediction]] is performed; perturbation data were **not used** for pretraining, fine-tuning, or evaluation. (Contrast embedding-shift perturbation in [[Geneformer]] and supervised models [[GEARS]] / [[CPA]] / [[scGen]].)

### 16. Batch correction or integration capability
Yes — a core capability. UCE aligns datasets, batches, and **species** into one space **zero-shot**, evaluated with the Single-Cell Integration Benchmark (scIB). This is embedding-level [[batch correction]] / [[data integration]], not generative correction of expression values.

## Evaluation

### 17. Benchmark and validation
Cell-type classification and batch-effect correction via **scIB** on datasets including **Tabula Sapiens v2** and the **Human Brain Cell Atlas**. Exact scores: `needs verification`. See [[cell embedding benchmark]], [[batch correction benchmark]], [[biological conservation benchmark]].

### 18. Disease or biological validation
Limited/indirect — the paper targets **broad cell biology**, not a specific disease, and makes **no disease-prediction claims**. Atlas mapping (e.g. the Human Brain Cell Atlas) could support disease-tissue annotation/integration, but do not infer clinical utility. See [[single-cell foundation models for disease biology]].

## Practical use

### 19. Strengths
Cross-species, vocabulary-free, zero-shot universal embeddings; novel protein-sequence grounding of genes; strong fit for integration/atlas mapping across heterogeneous datasets and species.

### 20. Limitations
Embedding-only output (no expression or perturbation prediction); zero-shot-only by design may trail task-tuned models; depends on the quality/coverage of protein-LM embeddings; 650M-param model has nontrivial compute cost; atlas coverage biases propagate into embeddings.

### 21. Best use cases
Cross-species cell annotation, atlas/query-to-reference mapping, and dataset integration where a shared gene vocabulary is unavailable — used zero-shot.

## Wiki links

### 22. Related models
[[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[GeneCompass]] (also cross-species), [[scPRINT]], [[CellPLM]]

### 23. Related papers
[[rosen-2023-universal-cell-embeddings|Rosen et al. 2023]] (UCE).

### 24. Tags
#scfm #model #transformer #zero-shot #cross-species
