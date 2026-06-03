---
title: condition token
aliases: [condition token, condition tokens, perturbation token]
type: concept
tags: [concept, scfm, perturbation]
status: stub
updated: 2026-06-03
---

# condition token

## Definition
A condition token is a special input token (or learned embedding) that encodes an experimental condition — such as a perturbation, batch, drug, or modality — alongside the gene tokens, so the model can condition its output on that context. A **perturbation token** is a condition token denoting a specific perturbation.

## Why it matters for scFMs
Condition tokens are the mechanism by which models perform **conditional generation** — e.g. predicting expression *under* a given perturbation or *in* a given batch. They are central to expression-level [[perturbation prediction]] and to batch-aware modeling.

## How it works / key distinctions
- During training, the model sees (cell, condition) pairs and learns how the condition shifts expression; at inference, swapping the condition token yields a predicted response.
- [[CPA]] explicitly disentangles a basal cell state from additive perturbation/covariate embeddings (condition embeddings).
- [[scGPT]] can incorporate condition/batch tokens for conditional tasks including perturbation fine-tuning (needs verification of exact token design).
- Distinct from [[rank-based encoding]]/[[expression value encoding]], which encode the gene/expression input, not the condition.

## Common pitfalls / what it is not
- A condition token enabling conditional generation does not by itself guarantee accurate transcriptome prediction — it must be trained on real perturbation data and benchmarked (see [[perturbation prediction]]).
- Conditioning on a batch token (for [[batch correction]]) is a different use than conditioning on a perturbation, though the mechanism is similar.
- Having a perturbation token is not the same as an embedding-shift method like [[Geneformer]]'s, which uses no learned perturbation token.

## Models / methods that use it
- [[CPA]] (perturbation/covariate embeddings), [[scGPT]] (condition/batch tokens, fine-tuned perturbation), [[scGen]] (latent arithmetic for conditions; needs verification).

## Related concepts
[[perturbation prediction]], [[in-silico perturbation]], [[tokenization-strategy|tokenization strategy]], [[batch correction]]

## Tags
#concept #scfm #perturbation #needs-verification
