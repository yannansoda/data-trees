---
{"topic":"AIxHealth","dg-publish":true,"permalink":"/LearningNotes/Omics Data Analysis/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"AIxHealth"}}
---

# What are Omics
Omics refers to large-scale, high-throughput fields of biology that systematically measure and characterize entire classes of molecules within a biological system. 

| Omics field         | What is measured              | Typical technologies                     |  Stability | Distance from current phenotype | Main question                                |
| ------------------- | ----------------------------- | ---------------------------------------- | ---------: | ------------------------------: | -------------------------------------------- |
| **Genomics**        | DNA sequence & variation      | Whole-genome sequencing, WES             |       High |                         Farther | What genetic variants does a person carry?   |
| **Transcriptomics** | RNA abundance & splicing      | RNA-seq, microarrays                     |     Medium |                    Intermediate | Which genes are being transcribed?           |
| **Proteomics**      | Proteins & modifications      | Mass spectrometry (LC-MS/MS), TMT/iTRAQ  | Medium-low |                          Closer | Which proteins are expressed or circulating? |
| **Metabolomics**    | Small molecules & metabolites | MS, NMR                                  |        Low |                      Very close | What is the current metabolic state?         |
| **Epigenomics**     | Chromatin state & methylation | ATAC-seq, ChIP-seq, bisulfite sequencing |            |                                 |                                              |

# Common Omics Data Analysis Workflow
1. Define biological / clinical question
2. Data preprocessing and QC
3. Normalization and transformation
4. Differential analysis
5. Dimensionality reduction and clustering
6. Functional interpretation
7. Validation and biological interpretation
# Common Analysis Methods
### Differential analysis
= comparisons between groups (e.g., disease vs control)
#### metrics
- (log2) **fold change** = a measure of how much a quantity changes between two conditions (e.g., treated vs control)
	- fold change ≥ 2 = upregulated proteins
	- fold change ≤ 0.5 = downregulated proteins
- p-values, FDR/adjusted p-values
#### visualization
- volcano plots
- heatmaps
- PCA/UMAP clustering ([[LearningNotes/Dimensionality Reduction\|Dimensionality Reduction]])
### Enrichment analysis
See [[LearningNotes/Enrichment Analysis\|LearningNotes/Enrichment Analysis]]
### Network analysis
#### PPI (Protein-Protein Interaction) network analysis
= constructs an interaction map using databases like STRING or BioGRID to reveal hubs and regulatory modules
### Multi-omics integration

# Specific Omics Analysis
- [[LearningNotes/Proteomics Analysis and Modeling\|Proteomics Analysis and Modeling]]
- Transcriptomics Analysis
- Genomics Analysis
- Metabolomics Analysis


