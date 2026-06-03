---
title: scMamba
aliases: [scMamba]
type: model
model_class: general-scfm
year: 2024
tags: [scfm, model, state-space-model, needs-verification]
status: stub
updated: 2026-06-03
---

# scMamba

> Organize around the workflow: **Input → Processing/Architecture → Output → Capabilities → Evaluation → Practical use.** Mark uncertain items `needs verification`. See [[AGENTS]] §5.
>
> **CAUTION:** scMamba is less established than the transformer scFMs, and the name may map to more than one preprint. Most specifics below are marked `needs verification` and should be confirmed against the primary source before use.

## 1. Overview
scMamba is a general [[single-cell foundation model]] (~2024) that replaces transformer self-attention with a selective state-space model (Mamba / SSM) backbone, aiming for linear-time scaling over long gene sequences. The exact paper, authorship, and design specifics need verification — the name may refer to more than one preprint.

## 2. Original paper
Original paper: **needs verification.** A 2024 preprint is the likely source, but identity (authors, title, venue) is not yet confirmed. Do not cite until verified. Summary: to be ingested (pending identification).

## 3. Model type
Pretrained [[single-cell foundation model]] using a state-space-model (Mamba/SSM) backbone instead of attention. Further classification needs verification.

## Input

### 4. Input format
scRNA-seq single-cell transcriptomes (assumed). Exact input format needs verification.

### 5. Tokenization or encoding strategy
Encoding strategy needs verification (e.g. gene identity tokens, [[rank-based encoding]], or [[expression value encoding|binned/continuous expression]] — unclear which). Do not assume.

### 6. Pretraining data
Pretraining corpus and #cells need verification. Perturbation data use: needs verification.

## Processing / Architecture

### 7. Architecture
Selective state-space model (Mamba / SSM) backbone replacing transformer attention, motivated by linear-time scaling over long gene sequences. Depth, dimensions, and parameter count need verification.

### 8. Training objective
Training objective needs verification (likely self-supervised masked/next-token prediction over gene sequences, but unclear).

### 9. Interpretability
Interpretability methods, if any, need verification.

## Output

### 10. Model output
Presumed [[cell embedding]] / [[gene embedding]] outputs; exact outputs need verification.

### 11. Output interpretation
Output interpretation needs verification. Do not assume transcriptome-level prediction vs embedding shift without the source.

## Capabilities
> Separate zero-shot, fine-tuning, and supervised perturbation prediction.

### 12. Supported tasks
Supported tasks need verification.

### 13. Zero-shot capability
[[zero-shot prediction|Zero-shot]] capability needs verification.

### 14. Fine-tuning capability
[[fine-tuning]] capability and typical heads need verification.

### 15. Perturbation capability
[[perturbation prediction]] capability needs verification (whether embedding shift, classifier shift, or transcriptome-level prediction is unknown; whether perturbation data were used is unknown).

### 16. Batch correction or integration capability
[[batch correction]] / [[data integration]] capability needs verification.

## Evaluation

### 17. Benchmark and validation
Benchmarks and metrics need verification.

### 18. Disease or biological validation
Disease/biological validation needs verification.

## Practical use

### 19. Strengths
Claimed strength is linear-time scaling over long gene sequences via an SSM backbone (needs verification). Other strengths unverified.

### 20. Limitations
Less established than transformer scFMs; ambiguous identity (possibly multiple preprints under the same name); nearly all specifics unverified.

### 21. Best use cases
Best use cases need verification. Treat as experimental until the source is confirmed.

## Wiki links

### 22. Related models
[[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[CellPLM]]

### 23. Related papers
Original paper needs verification (summary: to be ingested once identified).

### 24. Tags
#scfm #model #state-space-model #needs-verification
