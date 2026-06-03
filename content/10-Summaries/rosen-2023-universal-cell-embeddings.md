---
title: "Rosen 2023 — Universal Cell Embeddings (UCE)"
aliases: ["UCE paper"]
type: summary
model: "UCE"
year: 2023
venue: "bioRxiv"
tags: [summary, scfm, zero-shot, data-integration, cross-species]
status: reviewed
updated: 2026-06-03
---

# Rosen 2023 — Universal Cell Embeddings: A Foundation Model for Cell Biology

> Structured 24-field summary. Source-grounded; uncertain points marked `needs verification`. UCE produces a **[[cell embedding]]** zero-shot; it is **not** a perturbation-prediction model. Source note: [[rosen-2023-universal-cell-embeddings-source]].

## 1. Citation
Rosen Y, Roohani Y, Agrawal A, Samotorčan L, Tabula Sapiens Consortium, Quake SR, Leskovec J. *Universal Cell Embeddings: A Foundation Model for Cell Biology.* bioRxiv 2023. DOI: [10.1101/2023.11.28.568918](https://doi.org/10.1101/2023.11.28.568918). → [[rosen-2023-universal-cell-embeddings-source]]

## 2. Core question
Can a single self-supervised foundation model map **any** cell — across tissues and even across **species** — into one shared, biologically meaningful embedding space, **without** per-dataset retraining, annotations, or a fixed shared gene vocabulary?

## 3. Prior studies
Single-cell representation/integration methods (e.g. scVI, Harmony, scANVI) and earlier transformer scFMs such as [[scBERT]] and [[Geneformer]]; the authors' own cross-species integration work (SATURN). These rely on a fixed gene vocabulary and/or dataset-specific training.

## 4. Limitations of prior studies
Most methods assume a shared, fixed set of input genes, so they do not transfer to **new species** or unseen gene sets without retraining; many require fine-tuning or dataset-specific integration; cross-species alignment was handled separately rather than within one universal model.

## 5. What this study did
Introduced **UCE**, a transformer foundation model that represents each gene by its **protein-product embedding from a protein language model (ESM2)**, so cells from any species can be encoded without a shared gene vocabulary. A cell is turned into a "cell sentence" — a sample of its expressed genes, sampled with replacement weighted by expression. UCE is pretrained **self-supervised** and produces a universal [[cell embedding]] **zero-shot**. The authors also assemble a large Integrated Mega-scale Atlas (IMA) and show new datasets/species can be mapped into the same space.

## 6. Main results of this study
- A single embedding space organizes cells by cell type/lineage across tissues and **8 species** without labels.
- New datasets and **previously unseen species** can be embedded **zero-shot** (no fine-tuning) and align with the existing space.
- Competitive cell-type organization and batch integration on standard benchmarks (reported via the scIB metrics; see field 15).
- The authors report emergent biological structure (e.g. coherent organization of cell types/states) and the ability to help hypothesize/identify cell types for new data. (Exact quantitative claims: `needs verification` against the PDF.)

## 7. Limitations of this study
- Zero-shot only: **"UCE is not intended to be finetuned"**, which can cap task-specific performance versus tuned models.
- Depends on the quality/availability of protein-language-model embeddings for genes; non-coding/poorly-annotated genes are harder to represent (author framing; `needs verification`).
- Large model (650M params) → compute cost for embedding at scale.
- Atlas composition biases (species/tissue coverage) propagate into the embedding. Disease-specific validation is limited (broad cell-biology focus).

## 8. Methods
Self-supervised pretraining on a large multi-species single-cell corpus; cells encoded as expression-weighted samples of expressed genes; genes mapped to ESM2 protein embeddings plus genomic/chromosome positional information (positional details `needs verification`). Evaluation by embedding held-out/new datasets and measuring cell-type separation and batch integration with the Single-Cell Integration Benchmark (scIB).

## 9. Model architecture
Transformer encoder; the released main model is a **33-layer transformer with ~650 million parameters** (a smaller 4-layer model is also released). Output is a fixed-length universal [[cell embedding]] (commonly cited as 1280-dimensional; exact dimension `needs verification`).

## 10. Input data type
scRNA-seq / snRNA-seq single-cell gene-expression profiles (counts), across multiple species. No cell-type labels required at inference.

## 11. Tokenization or encoding strategy
Genes are **not** identity tokens from a fixed vocabulary. Each gene is represented by the **ESM2 protein language-model embedding** of its protein product, enabling cross-species and new-species transfer. A cell ("cell sentence") is a **sample of its expressed genes, drawn with replacement weighted by expression** — so expression magnitude enters via sampling frequency rather than as binned or raw value tokens. See [[tokenization strategy]]; this differs from [[rank-based encoding]] (Geneformer) and binned [[expression value encoding]] (scGPT/scBERT).

## 12. Pretraining data
**~36 million single-cell transcriptomes** spanning **8 species** (human, mouse, zebrafish, mouse lemur, crab-eating macaque, rhesus macaque, tropical clawed frog, pig) and dozens of tissues, aggregated into the Integrated Mega-scale Atlas (IMA). Exact dataset count: `needs verification`. **Perturbation data: not used.**

## 13. Fine-tuning strategy (if applicable)
**Not applicable / by design none.** UCE is used **zero-shot**; the authors state it "is not intended to be finetuned." See [[zero-shot prediction]] vs [[fine-tuning]].

## 14. Main tasks evaluated
Zero-shot [[cell embedding]] generation; cell-type organization/cell-type annotation (via embedding structure / label transfer); cross-species and cross-dataset [[data integration]] / [[batch correction]]; mapping new datasets onto the IMA (atlas mapping). **No perturbation-response prediction.**

## 15. Benchmark datasets and metrics
Cell-type classification and batch-effect correction evaluated with the **Single-Cell Integration Benchmark (scIB)** on datasets including **Tabula Sapiens v2** and the **Human Brain Cell Atlas**. Metrics: scIB biological-conservation and batch-correction scores (e.g. cell-type ASW/ARI/NMI, iLISI/kBET-type batch metrics). Exact numbers: `needs verification`. See [[batch correction benchmark]], [[biological conservation benchmark]], [[cell embedding benchmark]].

## 16. Perturbation analysis (if applicable)
**Not applicable.** UCE does not perform [[in silico perturbation]] or [[perturbation prediction]]; no perturbation data were used for pretraining, fine-tuning, or evaluation. (Contrast with general scFMs that demonstrate embedding-shift perturbation, e.g. [[Geneformer]], and with perturbation-specific models [[GEARS]] / [[CPA]] / [[scGen]].)

## 17. Batch correction or data integration (if applicable)
Yes — a central capability. UCE integrates datasets, batches, and **species** into one space **zero-shot**, evaluated with scIB. This is [[batch correction]] / [[data integration]] at the embedding level, not generative correction of expression values.

## 18. Interpretability or biological insight
The shared space shows coherent, label-free organization of cell types/lineages across species; the authors use it to map and help hypothesize cell identities for new data. Claims are about **embedding structure**, not mechanistic or causal biology. Specific case studies: `needs verification`.

## 19. Relevance to single-cell foundation models
A leading example of a **zero-shot, cross-species** [[single-cell foundation model]]. Its protein-embedding gene representation is a distinctive design choice in the scFM landscape (most peers use fixed gene-ID vocabularies). Strong reference point for [[cell embedding benchmark]] and integration comparisons.

## 20. Relevance to disease biology
Limited/indirect. The paper targets **broad cell biology**, not a specific disease. Universal embeddings and atlas mapping could support disease-tissue annotation/integration (e.g. brain via the Human Brain Cell Atlas), but the paper makes **no disease-prediction claims**. Do not infer clinical utility. See [[single-cell foundation models for disease biology]].

## 21. Connection to other papers or models
Model page: [[UCE]]. Compare with [[Geneformer]], [[scGPT]], [[scFoundation]], [[scBERT]], [[GeneCompass]] (also cross-species, knowledge-informed). Perturbation models for contrast: [[GEARS]], [[CPA]], [[scGen]]. Summaries for those: to be ingested.

## 22. Related concepts
[[single-cell foundation model]] · [[cell embedding]] · [[gene embedding]] · [[zero-shot prediction]] · [[fine-tuning]] · [[transfer learning]] · [[tokenization strategy]] · [[data integration]] · [[batch correction]] · cell-type annotation

## 23. Open questions
- How much does zero-shot-only use cost in task-specific accuracy vs fine-tuned scFMs?
- How robust are cross-species embeddings for distant species / poorly-annotated genomes?
- Quantitative standing vs other scFMs and simple baselines (HVG+PCA) under matched [[benchmarking single-cell foundation models|fair benchmarks]]? (`needs verification`)
- Utility for disease tissues (e.g. neurological) beyond annotation/integration?

## 24. Tags
#scfm #summary #zero-shot #data-integration #batch-correction #cross-species #cell-embedding
