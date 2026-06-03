---
title: benchmarking single-cell foundation models
aliases: [benchmarking single-cell foundation models, benchmarking scFMs, scFM benchmarking]
type: topic
tags: [topic, scfm, benchmark, needs-verification]
status: stub
updated: 2026-06-03
---

# benchmarking single-cell foundation models

## Scope
How [[single-cell foundation models|scFMs]] are evaluated, and the growing body of *independent* benchmarks that question whether scFMs deliver their claimed advantages. This topic emphasizes **fair protocols**: matching the capability class ([[zero-shot]] vs [[fine-tuning]]), tuning baselines properly, holding compute/data comparable, and reporting per-task and per-class results rather than single composite scores.

## Key questions
- Under fair conditions, do scFMs beat simpler baselines (scVI/scANVI, Harmony, PCA + kNN, logistic regression on HVGs)?
- Where is the line between zero-shot and fine-tuned results, and are papers explicit about it?
- Which tasks (annotation, integration, perturbation) actually show scFM advantages, and which don't?
- Are benchmark datasets leaking into pretraining corpora (train/test overlap)?

## Models involved
Benchmarks typically compare [[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[CellPLM]], [[UCE]], [[scPRINT]], [[GeneCompass]], [[scMamba]] against non-scFM baselines. The baselines are as important as the models: a benchmark is only as strong as its weakest-tuned baseline.

## Key papers
To be ingested via the paper workflow (see AGENTS.md §3). No summaries exist yet. Candidate independent-benchmark references (all needs-verification until ingested):
- Kedzierska et al. — assessment of zero-shot scFM embeddings vs baselines (Geneformer, scGPT) (needs verification).
- Boiarsky et al. — scBERT/scGPT vs simple baselines for annotation, reporting competitive logistic regression (needs verification).
- Liu et al. / other independent evaluations questioning scFM perturbation and integration claims (needs verification).
- scEval and related evaluation frameworks (needs verification).

Specific author/finding attributions above must be verified during ingestion before being treated as established.

## State of the evidence
- **Recurring independent finding (needs verification):** in **zero-shot** settings, scFM embeddings often do *not* beat well-tuned simple baselines for annotation and integration; sometimes they underperform them. Reported by multiple independent groups.
- **Where scFMs do better:** strongly *fine-tuned* settings on standard tasks, and some integration/annotation cases — but advantages shrink when baselines are tuned and compute is matched.
- **Perturbation:** several analyses report simple baselines (mean perturbed profile, control) are competitive on common metrics, casting doubt on headline perturbation-prediction gains (needs verification — see [[perturbation prediction models]]).
- **Methodological issues flagged:** unfair baselines, composite-metric obscuring, possible train/test leakage, and conflation of capability classes. These are the central reasons to read scFM claims cautiously.
- **Net assessment:** scFMs are useful tools but their universal superiority is **not** established; the honest position is task- and protocol-dependent advantage, with several claims still contested.

## Open questions
- What would a standardized, leakage-controlled, baseline-anchored scFM benchmark suite look like?
- How should compute and pretraining-data scale be normalized in comparisons?
- Do any scFM advantages hold up out-of-distribution (new tissues, platforms, species, disease states)?

## Related
- Benchmarks: [[zero-shot benchmark]], [[biological conservation benchmark]], [[cell type annotation benchmark]], [[batch correction benchmark]]
- Concepts: [[zero-shot]], [[fine-tuning]], [[cell embedding]], [[batch correction]]
- Topics: [[cell type annotation using foundation models]], [[batch correction and atlas integration]], [[perturbation prediction models]], [[virtual cell models and biological simulation]]

## Tags
#topic #scfm #benchmark #needs-verification
