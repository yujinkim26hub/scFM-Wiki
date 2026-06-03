---
title: perturbation prediction models
aliases: [perturbation prediction models, perturbation models]
type: topic
tags: [topic, scfm, perturbation, needs-verification]
status: stub
updated: 2026-06-03
---

# perturbation prediction models

## Scope
A survey of models that predict cellular response to perturbation, and the crucial distinction between two families that are often conflated:

1. **Supervised, perturbation-specific, transcriptome-level models** — [[GEARS]], [[CPA]], [[scGen]]. These are trained on perturbation data ([[Perturb-seq]], drug/dose, knockouts) and predict a *gene-expression profile* (a [[transcriptome-level prediction]]) for a perturbed condition. They are **not** pretrained [[single-cell foundation models|scFMs]].
2. **General scFMs used for in-silico perturbation** — [[Geneformer]] (in-silico deletion as an [[cell embedding|embedding]] shift), [[scGPT]] ([[fine-tuning|fine-tuned]] for perturbation response). The output type varies and is frequently *not* a full predicted transcriptome.

The core message of this page is **output-type discipline**: state exactly what each model emits.

## Key questions
- For each model: does it output a transcriptome-level expression prediction, an embedding/state shift, or a classifier-score change?
- Were perturbation data used for pretraining, fine-tuning, evaluation only, or not at all? (AGENTS.md §0.5)
- Are evaluations on seen perturbations, unseen single perturbations, or unseen combinations (the hard generalization case)?
- Do scFMs beat purpose-built supervised models (GEARS/CPA) on perturbation prediction, or only match simple baselines (e.g. predicting the mean perturbed state)?

## Models involved
| Model | Class | Output type | Perturbation data use |
|---|---|---|---|
| [[GEARS]] | supervised, perturbation-specific | transcriptome-level (post-perturbation expression), uses GO graph | trained on perturbation data |
| [[CPA]] | supervised (compositional autoencoder) | transcriptome-level, disentangled latent | trained on perturbation data |
| [[scGen]] | supervised (VAE + latent vector arithmetic) | transcriptome-level (predicted shifted profile) | trained on perturbation/condition data |
| [[Geneformer]] | general scFM | in-silico perturbation = [[cell embedding|embedding]] shift / state-classifier signal (not a transcriptome) | not pretrained on perturbation data (needs verification) |
| [[scGPT]] | general scFM | perturbation response via fine-tuned head; can emit expression-level outputs when fine-tuned for it | fine-tuned on perturbation data (needs verification) |
| [[scFoundation]] | general scFM | embeddings; has been paired with downstream perturbation tasks (needs verification) | not pretrained on perturbation data (needs verification) |

Details above need verification against ingested summaries.

## Key papers
To be ingested via the paper workflow (see AGENTS.md §3). No summaries exist yet. Candidate references (needs-verification until ingested):
- Roohani et al., GEARS (2023/2024) — graph-based perturbation prediction incl. combinations.
- Lotfollahi et al., CPA (2023) and scGen (2019) — compositional / latent-space response prediction.
- Theodoris et al., Geneformer (2023) — in-silico perturbation as embedding shift.

## State of the evidence
- **Demonstrated:** GEARS/CPA/scGen predict perturbation-shifted transcriptomes on benchmark Perturb-seq datasets; performance degrades for unseen combinations.
- **Contested:** several independent analyses report that simple baselines (e.g. predicting the dataset mean perturbed profile, or non-perturbed controls) are surprisingly competitive on common metrics, raising concerns about metric choice and task difficulty (needs verification — see [[benchmarking single-cell foundation models]]).
- **Frequently overclaimed:** scFM "in-silico perturbation" is often presented as response *prediction*. For [[Geneformer]] it is an embedding/state shift, not a predicted expression profile. Do not equate the two.
- **Separation required:** keep [[zero-shot]] scFM perturbation, fine-tuned scFM perturbation, and supervised transcriptome-level prediction as distinct claims.

## Open questions
- What is a fair, baseline-anchored benchmark for perturbation prediction?
- Can frozen scFM embeddings predict perturbation responses zero-shot, or is supervised fine-tuning always required?
- Do scFM priors actually help on unseen combinatorial perturbations?

## Related
- Concepts: [[perturbation prediction]], [[in silico perturbation]], [[transcriptome-level prediction]], [[cell embedding]], [[zero-shot]], [[fine-tuning]]
- Datasets: [[Perturb-seq]]
- Topics: [[single-cell foundation models for disease biology]], [[benchmarking single-cell foundation models]]

## Tags
#topic #scfm #perturbation #needs-verification
