---
title: gene relationship benchmark
aliases: [gene relationship benchmark, gene-relationship benchmark, gene relationship, gene-gene relationship benchmark, GRN benchmark]
type: benchmark
tags: [benchmark, scfm]
status: stub
updated: 2026-06-03
---

# gene relationship benchmark

## Task definition
Assess whether a model's learned gene representations or attention recover known gene-gene relationships — co-expression, pathway membership, regulatory (TF-target) links, or protein-protein interactions — by comparing model-derived gene similarities/edges against reference networks.

## Common datasets / references
- Reference networks: known GRNs, pathway databases (e.g. Reactome, KEGG), TF-target sets (e.g. from regulatory atlases), protein interaction databases (e.g. STRING). Specific references vary per paper (needs verification).
- Underlying expression from atlases such as [[CELLxGENE Census]] / [[Human Cell Atlas]].

## Metrics
- Precision / precision-at-k of recovered edges against a reference network.
- AUROC / AUPRC for ranking gene pairs as related vs not.
- Overlap/enrichment of co-embedded genes with pathways.
- Blind spots: reference networks are incomplete and biased toward well-studied genes; "false positives" may be true-but-unannotated. AUROC is sensitive to the negative set. Recovering correlation/co-expression is **not** evidence of causal regulation (correlation ≠ causation).

## How models are evaluated here
- **Zero-shot**: extract gene embeddings or attention from a frozen scFM and score against reference networks (most common).
- **Fine-tuned / task-specific**: a GRN-inference head or downstream model trained on top.
- Report which; zero-shot gene-embedding geometry and a trained GRN predictor are different claims.

## Models evaluated
- [[Geneformer]] — reported in-silico/attention analyses related to gene networks (source/summary needed).
- [[scGPT]] — gene-embedding similarity / GRN-style analyses reported.
- [[GeneCompass]] — incorporates prior knowledge (e.g. regulatory priors) relevant here (needs verification).
- [[scPRINT]] — targets gene-network inference (needs verification of exact benchmark).
- [[GEARS]] — uses gene-relationship graphs as input prior, not purely as an evaluation target.

## Caveats
- A recovered edge reflects statistical association in the training corpus, not validated mechanism.
- Reference-network incompleteness makes both precision and recall hard to interpret as absolute truth.
- Hub/highly-expressed genes can dominate similarity, inflating apparent recovery.
- Cross-paper comparability limited by differing reference sets and thresholds.

## Related
- [[perturbation prediction benchmark]]
- [[CELLxGENE Census]]
- [[Geneformer]], [[scGPT]], [[scPRINT]], [[GeneCompass]]

## Tags
#benchmark #scfm
