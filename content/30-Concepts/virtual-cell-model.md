---
title: virtual cell model
aliases: [virtual cell model, virtual cell, AI virtual cell]
type: concept
tags: [concept, scfm]
status: stub
updated: 2026-06-03
---

# virtual cell model

## Definition
A virtual cell model (or "AI virtual cell") is an aspirational in-silico model that would simulate the state and behavior of a cell — including its response to perturbations, signals, and environment — across modalities and conditions. It is a stated *goal* of the field, not an achieved system.

## Why it matters for scFMs
[[single-cell foundation model|scFMs]] are frequently framed as building blocks toward a virtual cell: a model that learns broad cellular representations and can, in principle, be queried for predicted responses. The vision motivates large pretraining efforts, but the gap between today's representation models and a faithful, validated virtual cell is large.

## How it works / key distinctions
- The concept spans multiple capabilities that are usually evaluated separately today: representation ([[cell embedding]]), [[in-silico perturbation]], [[perturbation prediction]], and generation of full transcriptomes.
- A true virtual cell would predict the *transcriptome-level* response to an arbitrary perturbation, not merely a [[cell-state shift|shift in embedding space]] or a [[classifier-score shift]].

## Common pitfalls / what it is not
- Do not equate an scFM with a virtual cell. Producing a [[cell embedding]] is not simulating a cell.
- Claims that a model "is" or "achieves" a virtual cell should be treated skeptically; the term is largely programmatic and forward-looking (needs verification of any specific claim).
- A movement in latent space ([[cell-state shift]]) is not the same as a validated biological prediction.

## Models / methods that use it
- Framed as contributors toward the goal: [[scGPT]], [[scFoundation]], [[UCE]], [[Geneformer]], [[CellPLM]] (authors' framing varies; needs verification).
- Perturbation-response components draw on [[GEARS]], [[CPA]], [[scGen]].

## Related concepts
[[single-cell foundation model]], [[in-silico perturbation]], [[perturbation prediction]], [[cell-state shift]], [[cell embedding]]

## Tags
#concept #scfm #perturbation #needs-verification
