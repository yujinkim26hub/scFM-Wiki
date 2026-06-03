---
title: "<First author> <Year> — <short title>"
aliases: ["<firstauthor-year-slug>"]
type: summary
model: "<model name or n/a>"
year: <YYYY>
venue: "<journal / venue>"
tags: [summary, scfm, needs-verification]
status: stub
updated: <YYYY-MM-DD>
---

# <First author> <Year> — <Title>

> Structured summary. Fill only what the source supports. Mark anything uncertain `unclear` or `needs verification`; mark inapplicable fields `not applicable`. Do not speculate. See [[AGENTS]] §4.

## 1. Citation
<Authors. Title. Venue. Year. DOI/URL.>  → source note: [[<firstauthor-year-slug>]]

## 2. Core question
<What problem does the paper address?>

## 3. Prior studies
<Key prior work the paper builds on / positions against.>

## 4. Limitations of prior studies
<Gaps the paper identifies in prior work.>

## 5. What this study did
<One-paragraph summary of the contribution.>

## 6. Main results of this study
<Headline findings, with numbers where given.>

## 7. Limitations of this study
<Limitations stated by the authors, plus obvious ones — labeled as your inference.>

## 8. Methods
<Data processing, training setup, evaluation protocol.>

## 9. Model architecture
<Backbone (transformer / Mamba / GNN / VAE…), depth, params if reported.>

## 10. Input data type
<scRNA-seq / snRNA-seq / scATAC-seq / multi-omics; counts vs normalized; species.>

## 11. Tokenization or encoding strategy
<Gene identity tokens / rank-based ordering / binned expression / raw value / condition tokens / metadata. Be precise.>

## 12. Pretraining data
<Corpus, #cells, #genes, source atlases. State whether perturbation data were included.>

## 13. Fine-tuning strategy (if applicable)
<Task heads, frozen vs full fine-tune, or "not applicable".>

## 14. Main tasks evaluated
<e.g. cell type annotation, batch integration, GRN inference, perturbation prediction.>

## 15. Benchmark datasets and metrics
<Datasets + metrics (accuracy, F1, ARI, NMI, scIB, Pearson delta, MSE…).>

## 16. Perturbation analysis (if applicable)
<Was perturbation data used for pretrain / fine-tune / eval / not used? Embedding shift vs classifier shift vs transcriptome-level prediction? Or "not applicable".>

## 17. Batch correction or data integration (if applicable)
<How evaluated (scIB), or "not applicable".>

## 18. Interpretability or biological insight
<Attention analysis, in silico perturbation findings, biomarkers — only what the paper claims.>

## 19. Relevance to single-cell foundation models
<How it advances / relates to the scFM landscape.>

## 20. Relevance to disease biology
<Disease applications shown; note neuro relevance if any. Do not overreach.>

## 21. Connection to other papers or models
<Wikilinks: [[Geneformer]], [[scGPT]], related summaries.>

## 22. Related concepts
<[[gene embedding]], [[zero-shot prediction]], …>

## 23. Open questions
<Unresolved issues / future work.>

## 24. Tags
#scfm #summary <#perturbation #zero-shot #neuro …>
