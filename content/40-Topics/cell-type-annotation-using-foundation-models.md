---
title: cell type annotation using foundation models
aliases: [cell type annotation using foundation models, annotation using foundation models, scFM cell type annotation]
type: topic
tags: [topic, scfm, annotation, needs-verification]
status: stub
updated: 2026-06-03
---

# cell type annotation using foundation models

## Scope
Use of [[single-cell foundation models|scFMs]] to assign cell-type labels to single-cell data — the most mature scFM application. Covers three modes that must be kept distinct:

- **[[zero-shot]] embedding + clustering/kNN:** use frozen scFM embeddings, then cluster or transfer labels by nearest neighbors from a reference. No task-specific training.
- **[[fine-tuning|fine-tuned]] classification:** attach a classifier head and train on labeled data; usually the strongest scFM annotation mode.
- **Reference-based mapping:** project a query onto a labeled reference atlas and transfer labels (overlaps with [[batch correction and atlas integration]]).

## Key questions
- How much does fine-tuning beat zero-shot for annotation, and on which datasets?
- Do scFMs outperform standard supervised classifiers (logistic regression / SVM on HVGs, scANVI label transfer) once those are fairly tuned?
- How well do scFMs annotate *rare* and *novel* cell types, and out-of-distribution tissues?
- How stable are labels across batches, platforms, and species?

## Models involved
- [[scGPT]] — commonly fine-tuned for annotation; reports strong supervised results (needs verification).
- [[Geneformer]] — annotation via embeddings + fine-tuning; rank-based encoding.
- [[scBERT]] — introduced with cell-type annotation as a primary task (needs verification).
- [[scFoundation]], [[CellPLM]], [[UCE]], [[scPRINT]], [[GeneCompass]], [[scMamba]] — embedding sources for zero-shot or fine-tuned annotation.
- Baselines (scANVI, CellTypist, simple linear classifiers) are the key comparators; see [[cell type annotation benchmark]].

## Key papers
To be ingested via the paper workflow (see AGENTS.md §3). No summaries exist yet. Candidate references (needs-verification): Yang et al., scBERT (2022); Cui et al., scGPT (2024); Theodoris et al., Geneformer (2023).

## State of the evidence
- **Demonstrated:** fine-tuned scFMs achieve competitive-to-strong cell-type annotation accuracy on standard datasets. This is the best-supported scFM capability.
- **Contested for zero-shot:** independent [[benchmarking single-cell foundation models|benchmarks]] report that *zero-shot* scFM embeddings do **not** consistently beat simpler baselines for annotation, and sometimes underperform them (needs verification).
- **Weaker for rare/novel types:** performance on rare or unseen cell types and OOD tissues is less established; high overall accuracy can mask poor rare-class recall.
- **Protocol matters:** results depend heavily on whether the comparison is zero-shot vs fine-tuned and on baseline tuning quality. Always report which mode was used.

## Open questions
- When (if ever) is a frozen scFM embedding better than a tuned simple classifier for annotation?
- Can scFMs reliably flag novel cell types rather than forcing them into known classes?
- How well do annotations transfer across species and platforms zero-shot?

## Related
- Concepts: [[cell type annotation]], [[zero-shot]], [[fine-tuning]], [[cell embedding]], [[data integration]]
- Benchmarks: [[cell type annotation benchmark]], [[zero-shot benchmark]]
- Topics: [[batch correction and atlas integration]], [[benchmarking single-cell foundation models]]

## Tags
#topic #scfm #annotation #needs-verification
