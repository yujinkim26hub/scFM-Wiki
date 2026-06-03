---
title: zero-shot capability comparison
aliases: [zero-shot capability comparison]
type: comparison
criterion: zero-shot capability
tags: [comparison, scfm, zero-shot, needs-verification]
status: stub
updated: 2026-06-03
---

# zero-shot capability comparison

> Compares models on a **single shared criterion**: what each can do **frozen / zero-shot** (no fine-tuning). Do **not** rank models or declare a winner. Mark gaps `needs verification`. See [[AGENTS]] §6.

## Criterion
What works with frozen weights and no task-specific training — typically reuse of embeddings for clustering / annotation / similarity. This is the **zero-shot** capability class, kept distinct from fine-tuning and supervised perturbation ([[AGENTS]] §0.2). Contested cases are flagged explicitly.

## Comparison table

| Model | What is known | Evidence / source paper | Interpretation | Limitations / uncertainty |
|---|---|---|---|---|
| [[Geneformer]] | Zero-shot embeddings available; classification needs fine-tuning. | Theodoris 2023, Nature (needs verification) | Frozen embeddings usable; label tasks are not zero-shot. | needs verification. |
| [[scGPT]] | Zero-shot performance is contested. | Cui 2024, Nat Methods (needs verification) | Reports of frozen-embedding quality vary. | Contested; needs verification. |
| [[scFoundation]] | Embeddings usable without fine-tuning (extent needs verification). | Hao 2024, Nat Methods (needs verification) | Frozen embeddings as features. | Zero-shot scope needs verification. |
| [[scBERT]] | Annotation reported via fine-tuned classifier, not zero-shot. | Yang 2022, Nat Mach Intell (needs verification) | Main task needs fine-tuning. | Zero-shot embedding use needs verification. |
| [[scMamba]] | needs verification. | ~2024 (needs verification) | needs verification. | Zero-shot status needs verification. |
| [[CellPLM]] | needs verification. | Wen 2024, ICLR (needs verification) | Frozen embedding use plausible but unconfirmed. | needs verification. |
| [[scPRINT]] | needs verification. | Kalfon ~2024 (needs verification) | needs verification. | Zero-shot status needs verification. |
| [[UCE]] | Zero-shot universal cell embeddings; authors state it is "not intended to be finetuned"; embeds unseen species. | [[rosen-2023-universal-cell-embeddings|Rosen 2023]] | Designed for frozen, vocabulary-free use across datasets and species. | Zero-shot accuracy vs tuned models / simple baselines needs verification. |
| [[GeneCompass]] | Embeddings usable across species (zero-shot extent needs verification). | Yang 2024 (needs verification) | Cross-species frozen embeddings plausible. | needs verification. |
| [[GEARS]] | n/a — supervised perturbation model; not used zero-shot. | Roohani 2023, Nat Biotech (needs verification) | Requires perturbation training data. | — |
| [[CPA]] | n/a — supervised model; not used zero-shot. | Lotfollahi 2023, Mol Syst Biol (needs verification) | Requires condition-labeled training. | — |
| [[scGen]] | n/a — supervised VAE; not used zero-shot. | Lotfollahi 2019, Nat Methods (needs verification) | Requires condition-labeled training. | — |

## Notes
- [[UCE]] is explicitly designed for zero-shot use; [[Geneformer]] offers zero-shot embeddings but not zero-shot classification; [[scGPT]] zero-shot quality is contested.
- Perturbation-specific models are supervised and have no zero-shot mode; see [[model type comparison]].

## Related
- [[fine-tuning capability comparison]] · [[supported tasks comparison]] · [[output interpretation comparison]] · [[training objective comparison]] · [[model comparison overview]]

## Tags
#comparison #scfm #zero-shot #needs-verification
