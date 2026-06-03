---
title: virtual cell models and biological simulation
aliases: [virtual cell models and biological simulation, virtual cell models, virtual cell, AI virtual cell]
type: topic
tags: [topic, scfm, virtual-cell, needs-verification]
status: stub
updated: 2026-06-03
---

# virtual cell models and biological simulation

## Scope
The aspiration that [[single-cell foundation models|scFMs]] are steps toward a [[virtual cell model]] — a computational system that can *simulate* a cell's state and its response to arbitrary perturbations, conditions, or genotypes across contexts. This topic separates the **vision** from **current capability**, and states the gap honestly.

The "AI virtual cell" framing (a model that predicts cellular behavior in silico, enabling experiments to be run computationally) has been promoted in the field. It is a long-horizon goal, not a description of what today's scFMs do.

## Key questions
- What would a virtual cell model actually need to do (universal, multi-context, [[transcriptome-level prediction|transcriptome-level]], causal, generalizing to unseen perturbations)?
- How far are current scFMs from that — and which specific capabilities are missing?
- Is predicting an [[cell embedding|embedding]] shift ever sufficient, or is a true expression/state simulation required?
- What evaluation would credibly demonstrate "simulation" rather than interpolation within training distribution?

## What a virtual cell would require (vs current state)
| Requirement | Current scFM status |
|---|---|
| Predict full post-perturbation transcriptome | Mostly no; general scFMs emit embeddings/state shifts. Supervised models ([[GEARS]], [[CPA]], [[scGen]]) predict expression but only within trained regimes (needs verification) |
| Generalize to unseen perturbations/combinations | Weak; combinatorial generalization is poor (needs verification) |
| Causal / mechanistic, not correlational | Not demonstrated; models are largely correlational |
| Multi-context (tissue, species, condition, time) | Partial embeddings exist (e.g. [[UCE]] cross-species), but not validated simulation |
| Dynamics / time evolution | Largely absent in current scFMs |
| Experimentally validated predictions | Rare; most results are retrospective |

## Models involved
- General scFMs ([[Geneformer]], [[scGPT]], [[scFoundation]], [[UCE]], [[CellPLM]], [[scPRINT]], [[GeneCompass]], [[scBERT]], [[scMamba]]) are sometimes framed as virtual-cell building blocks, but they provide representations/annotations, not validated simulation.
- Perturbation-specific [[perturbation prediction models]] ([[GEARS]], [[CPA]], [[scGen]]) are closest to "simulation" in that they output transcriptomes, but only for trained perturbation regimes.

## Key papers
To be ingested via the paper workflow (see AGENTS.md §3). No summaries exist yet. The "AI Virtual Cell" perspective (Bunne et al. / community perspective pieces, ~2024) is relevant as a vision statement (needs verification) and is not evidence of capability.

## State of the evidence
- **Aspirational:** the virtual cell is a stated goal, not a demonstrated capability. No current model simulates a cell's full response to arbitrary perturbations across contexts.
- **What exists today:** representation learning (embeddings), annotation, integration, and limited perturbation prediction within training distribution. These are components, not a virtual cell.
- **The gap:** missing pieces include causal grounding, robust unseen-perturbation generalization, dynamics, multi-context transfer, and experimental validation. See [[benchmarking single-cell foundation models]] for evidence that even narrower claims are contested.
- **Honest assessment:** treat "virtual cell" language as motivation, not achievement. Do not describe any current scFM as a virtual cell.

## Open questions
- What benchmark would distinguish genuine simulation from in-distribution interpolation?
- Can scaling current scFMs ever yield causal/mechanistic prediction, or is a different paradigm needed?
- Is transcriptome-only data sufficient, or are multi-omic/perturbation/temporal data prerequisites?

## Related
- Concepts: [[virtual cell model]], [[in silico perturbation]], [[transcriptome-level prediction]], [[cell embedding]]
- Topics: [[perturbation prediction models]], [[benchmarking single-cell foundation models]], [[single-cell foundation models for disease biology]]

## Tags
#topic #scfm #virtual-cell #needs-verification
