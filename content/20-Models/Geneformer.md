---
title: Geneformer
aliases: [Geneformer]
type: model
model_class: general-scfm
year: 2023
tags: [scfm, model, transformer, needs-verification]
status: stub
updated: 2026-06-03
---

# Geneformer

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.

## 1. Overview
Geneformer is a general [[single-cell foundation model]] introduced by Theodoris et al. (Nature, 2023). It is an encoder-only (BERT-like) transformer pretrained self-supervised on a large human single-cell transcriptome corpus. The authors present it as a context-aware model for network biology and transfer learning to downstream single-cell tasks with limited labeled data.

## 2. Original paper
[[theodoris-2023-geneformer|Theodoris et al. 2023]] — "Transfer learning enables predictions in network biology", Nature 2023. Summary: to be ingested.

## 3. Model type
Pretrained [[single-cell foundation model]] (encoder-only transformer, self-supervised). Not a supervised perturbation model.

## Input

### 4. Input format
scRNA-seq / snRNA-seq single-cell transcriptomes. Per-cell gene expression is used to derive a rank ordering of genes; expression is not passed as explicit value tokens. Number of genes considered per cell is bounded by the input sequence length (exact length needs verification).

### 5. Tokenization or encoding strategy
[[rank-based encoding]]. Each gene in a cell is ranked by its expression after normalizing that gene by its non-zero median expression across the pretraining corpus. The cell is then represented as the ordered sequence of gene-identity tokens (highest-rank genes first). There are no explicit [[expression value encoding|expression-value tokens]] — expression information enters only through the rank ordering. No [[condition token]] in the base model.

### 6. Pretraining data
"Genecorpus-30M" (~30M human single cells; exact size needs verification). Drawn from a broad collection of public human scRNA-seq datasets (source atlases need verification). A later update reportedly scaled the corpus to ~95M cells (needs verification). Perturbation data: not used for pretraining (needs verification).

## Processing / Architecture

### 7. Architecture
Encoder-only transformer (BERT-style). Layer count, hidden size, and parameter count need verification.

### 8. Training objective
Self-supervised masked gene prediction: a subset of gene tokens in the ranked sequence is masked and the model predicts the masked genes from context.

### 9. Interpretability
The authors use attention/embedding analyses and [[in silico perturbation]]: deleting or inserting gene tokens and measuring the resulting shift in the [[cell embedding]] / predicted cell state. They apply this to network biology and gene-importance analyses.

## Output

### 10. Model output
Contextual [[gene embedding]]s and a [[cell embedding]]. With a task head added during [[fine-tuning]], it can output class labels (e.g. cell types).

### 11. Output interpretation
[[in silico perturbation]] in Geneformer produces a **[[cell embedding]] / cell-state shift**, not a transcriptome-level expression prediction. The shift indicates a change in predicted cell state, not predicted post-perturbation gene expression. Frozen embeddings are usable zero-shot; classification requires fine-tuning.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction.

### 12. Supported tasks
[[cell type annotation]] (fine-tuned), gene-network / GRN biology, gene-importance and [[in silico perturbation]] analyses.

### 13. Zero-shot capability
Frozen contextual gene and cell embeddings are usable [[zero-shot prediction|zero-shot]] for embedding-based analyses. Classification tasks generally need fine-tuning.

### 14. Fine-tuning capability
[[fine-tuning]] with a task head (e.g. a classification head) for cell type annotation and other supervised tasks; reported as effective with limited labeled data.

### 15. Perturbation capability
[[in silico perturbation]] via deletion/insertion of gene tokens, read out as a **cell-embedding / state shift** (not transcriptome-level [[perturbation prediction]]). Perturbation data were not used for pretraining; in the original paper perturbation analysis is an in-silico/evaluation use of the model rather than supervised training on perturbation outcomes (needs verification).

### 16. Batch correction or integration capability
[[batch correction]] / [[data integration]] behavior is not the model's primary advertised use; reported behavior needs verification.

## Evaluation

### 17. Benchmark and validation
The authors report transfer-learning results across several downstream single-cell tasks and network-biology analyses (specific benchmarks and metrics need verification). Link [[Benchmarks]] pages when ingested.

### 18. Disease or biological validation
The original paper includes a cardiac / cardiomyopathy application demonstrating network-biology predictions (specific disease claims need verification). No broader clinical conclusions beyond the paper.

## Practical use

### 19. Strengths
Large pretraining corpus; rank-based encoding avoids dependence on absolute expression scaling; effective transfer learning with limited labels (as reported).

### 20. Limitations
Rank-based input discards explicit expression magnitudes. In-silico perturbation outputs are state shifts, not expression predictions. Exact corpus size, architecture details, and benchmark specifics need verification.

### 21. Best use cases
Embedding extraction for network biology, cell type annotation via fine-tuning, and in-silico gene-importance / perturbation screening interpreted at the cell-state level.

## Wiki links

### 22. Related models
[[scGPT]], [[scFoundation]], [[scBERT]], [[scMamba]], [[CellPLM]]

### 23. Related papers
[[theodoris-2023-geneformer|Theodoris et al. 2023]] (summary: to be ingested)

### 24. Tags
#scfm #model #transformer #zero-shot #needs-verification
