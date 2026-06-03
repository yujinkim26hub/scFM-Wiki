---
title: batch correction and atlas integration
aliases: [batch correction and atlas integration, atlas integration, batch correction and integration]
type: topic
tags: [topic, scfm, batch-correction, needs-verification]
status: stub
updated: 2026-06-03
---

# batch correction and atlas integration

## Scope
Use of [[single-cell foundation models|scFMs]] for [[batch correction]], [[data integration]], and reference-atlas mapping — removing technical/batch variation while preserving biological signal, and projecting query datasets onto a reference. This overlaps with [[cell type annotation using foundation models]] (reference mapping is often the substrate for label transfer).

The promise is that a model pretrained across many datasets learns a batch-invariant representation, so embedding new data into that space integrates it "for free." Whether scFMs do this better than dedicated integration methods (e.g. Harmony, scVI/scANVI, scVI-based pipelines) is the empirical question.

## Key questions
- Do scFM embeddings integrate batches [[zero-shot]], or is [[fine-tuning]] needed for competitive integration?
- How is the trade-off between batch mixing and [[biological conservation benchmark|biological conservation]] handled and measured (e.g. scIB-style metrics)?
- Do scFMs outperform scVI/scANVI/Harmony on standard integration benchmarks, or roughly match them at much higher cost (needs verification)?
- Does pretraining scale (more datasets) translate into better integration generalization?

## Models involved
- [[scGPT]] — reports integration/atlas-level tasks, often with fine-tuning (needs verification).
- [[Geneformer]] — embeddings used for integration; rank-based encoding gives some intrinsic robustness to depth/normalization (needs verification).
- [[scFoundation]], [[UCE]], [[CellPLM]], [[scPRINT]], [[GeneCompass]], [[scBERT]], [[scMamba]] — general scFMs producing cell embeddings usable for integration/mapping.
- [[UCE]] is notable for a universal cross-species embedding aim relevant to cross-dataset integration (needs verification).
- Non-scFM baselines (scVI, scANVI, Harmony) are the key comparators and should appear on the [[batch correction benchmark]].

## Key papers
To be ingested via the paper workflow (see AGENTS.md §3). No summaries exist yet. Integration is commonly evaluated with scIB metrics (Luecken et al., 2022; needs verification) — relevant as the benchmark framework, not an scFM paper.

## State of the evidence
- **Demonstrated:** scFM embeddings can integrate multi-batch datasets and support reference mapping; several scFM papers report competitive scIB-style scores on their chosen datasets.
- **Contested / needs verification:** whether scFMs beat well-tuned scVI/scANVI/Harmony. Independent [[benchmarking single-cell foundation models|benchmarks]] suggest that on some integration tasks, especially [[zero-shot]], simpler dedicated methods are competitive or better (needs verification).
- **Metric caveat:** integration scores trade off batch mixing against biological conservation; a single composite number can hide regressions. Always check both axes via a [[batch correction benchmark]].

## Open questions
- Is there a consistent advantage to scFM integration once compute is held fixed?
- How robust is scFM integration to strong batch effects, new platforms, or cross-species data?
- Does fine-tuning for integration harm transferability to other tasks?

## Related
- Concepts: [[batch correction]], [[data integration]], [[cell embedding]], [[zero-shot]], [[fine-tuning]]
- Benchmarks: [[batch correction benchmark]], [[biological conservation benchmark]]
- Topics: [[cell type annotation using foundation models]], [[benchmarking single-cell foundation models]]

## Tags
#topic #scfm #batch-correction #needs-verification
