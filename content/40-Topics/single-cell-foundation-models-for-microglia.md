---
title: single-cell foundation models for microglia
aliases: [single-cell foundation models for microglia, scFMs for microglia, foundation models for microglia]
type: topic
tags: [topic, scfm, disease, neuro, microglia, needs-verification]
status: stub
updated: 2026-06-03
---

# single-cell foundation models for microglia

## Scope
Use of [[single-cell foundation models|scFMs]] to study microglial states from single-cell/single-nucleus data, and their relevance to Alzheimer's disease (AD) and other neurodegeneration. A narrow specialization of [[single-cell foundation models for neurological disease]].

Microglia exist along a spectrum of states — homeostatic microglia and disease-associated microglia (DAM, also discussed as activated/MGnD states) — that shift in neurodegeneration. These states are defined by relatively subtle, continuous transcriptomic programs, which makes them a stringent test of whether scFM embeddings capture fine-grained, disease-relevant heterogeneity rather than just coarse cell types.

## Key questions
- Can scFM embeddings separate homeostatic vs DAM/activated microglial states [[zero-shot]], or only after [[fine-tuning]] on labeled microglia data?
- Are microglial substates (rare, continuous) well represented in scFM pretraining corpora, or washed out?
- Does in-silico perturbation of microglial risk genes (e.g. TREM2, APOE) produce anything interpretable beyond an [[cell embedding|embedding]] shift?
- Do scFMs add value over established microglia-focused analysis pipelines?

## Models involved
- [[Geneformer]], [[scGPT]] — candidate tools for embedding and annotating microglia; dedicated microglia evaluations are essentially absent in the primary scFM papers (needs verification).
- [[scFoundation]], [[CellPLM]], [[UCE]], [[scPRINT]], [[scBERT]], [[GeneCompass]], [[scMamba]] — usable as embedding sources; no known microglia-specific validation (needs verification).
- This is largely **open territory**: there is little published, microglia-specific scFM work to cite.

## Key papers
To be ingested via the paper workflow (see AGENTS.md §3). No summaries exist yet, and to current knowledge there are few or no scFM papers centered on microglia specifically (needs verification). DAM concept originates outside the scFM literature (Keren-Shaul et al., 2017; needs verification) and is referenced here as biological background only.

## State of the evidence
- **Essentially open:** there is little direct evidence on how well scFMs resolve microglial substates. Claims should be treated as untested hypotheses.
- **Plausible but unverified:** that scFMs can flag DAM-like states in AD tissue. No benchmark-grade validation is known (needs verification).
- **Caution:** microglial state differences are subtle and continuous; coarse cell-type benchmarks do *not* demonstrate that an scFM resolves homeostatic-vs-DAM transitions.

## Open questions
- Are DAM/activated states recoverable from frozen scFM embeddings, or do they require fine-tuning?
- How sensitive are scFM microglia embeddings to platform (scRNA-seq vs snRNA-seq) and to post-mortem artifacts?
- Can in-silico perturbation recapitulate known microglial state transitions?

## Related
- Datasets: [[microglia single-cell datasets]], [[single-cell brain atlas datasets]]
- Topics: [[single-cell foundation models for neurological disease]], [[single-cell foundation models for disease biology]]
- Concepts: [[cell type annotation]], [[in silico perturbation]], [[zero-shot]], [[fine-tuning]], [[cell embedding]]

## Tags
#topic #scfm #disease #neuro #microglia #needs-verification
