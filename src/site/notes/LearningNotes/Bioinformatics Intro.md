---
{"topic":"AIxHealth","dg-publish":true,"permalink":"/LearningNotes/Bioinformatics Intro/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"AIxHealth"}}
---

# What is Bioinformatics
Bioinformatics is the use of computational methods to store, analyze, interpret, and model biological data.

>[!Tip] Bioinformatics often focuses on biological data analysis, while computational biology often focuses more on modeling biological systems.

# Bioinformatics Subfields

| Subfield                                                 | Focus                                                                    | Applications                                                                                   |
| -------------------------------------------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- |
| Genomics ([[LearningNotes/Omics Data Analysis#What are Omics\|Omics Data Analysis#What are Omics]])        | sequencing, assembling, analyzing genome                                 | genome sequencing, genetic variation studies, gene expression analysis                         |
| Transcriptomics ([[LearningNotes/Omics Data Analysis#What are Omics\|Omics Data Analysis#What are Omics]]) | RNA transcripts produced by the genome                                   | gene expression profiling, disease diagnosis, understanding cell behavior                      |
| Proteomics ([[LearningNotes/Omics Data Analysis#What are Omics\|Omics Data Analysis#What are Omics]])      | protein structures, functions, and interactions                          | protein identification in diseases, biomarker discovery, drug-target identification            |
| Metabolomics ([[LearningNotes/Omics Data Analysis#What are Omics\|Omics Data Analysis#What are Omics]])    | metabolites and metabolic processes                                      | biomarker discovery, disease metabolism analysis, personalized medicine                        |
| Structural bioinformatics                                | 3D structure of biological macromolecules (e.g. proteins, nucleic acids) | protein folding analysis, drug design, enzyme mechanism studies                                |
| Pharmacogenomics                                         | drug-gene interactions                                                   | tailoring drug prescriptions, improving therapeutic efficacy, reducing side effects            |
| Systems biology                                          | modeling of biological networks and systems                              | understanding cellular networks, modeling disease mechanisms, gene-regulatory network analysis |
| Cheminformatics                                          | chemical data for biological applications                                | drug discovery, analyzing chemical libraries, predicting compound effects                      |
| Epigenomics                                              | chemical modifications in gene expression                                | cancer gender regulation, aging studies, understanding inheritance patterns                    |

# Bioinformatics Databases
| Database Type        | Definition                                                                                     | Key Features                                                                                          | Examples                              |
| -------------------- | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------- |
| primary              | repositories that contains original biological data                                            | raw data; frequently updated                                                                          | GenBank/NCBI, EMBL-EBI, DDBJ          |
| secondary            | data compiled from primary databases: adding curated, value-added information like annotations | curation and annotation of data; provides additional context and insights                             | UniProt, Pfam, RefSeq                 |
| derived / integrated | data derived from primary and secondary databases through computational analysis               | integration of data from multiple sources; provides comprehensive insights and functional annotations | Ensembl, Gene Ontology (GO), InterPro |

# Sequence Analysis
## Pairwise Sequence Alignment
= Aligning two biological sequences (DNA, RNA, or protein) to find similarity, differences, and evolutionary relationships.
### Main types
- **Global alignment**: align entire sequences end-to-end
- **Local alignment**: find best matching subsequences
### Key components
- **Scoring system**
    - Match (e.g., +1)
    - Mismatch (e.g., −1)
    - Gap penalty (penalty for insertions/deletions)
- **Gap penalties**
    - Linear: same cost per gap
    - **Affine gap penalty (more realistic):**
	    - Gap penalty=gap opening+(gap length×gap extension)
        - Gap opening penalty: high
        - Gap extension penalty: lower
> [!Tips] 
> A **gap** is an artificial placeholder (-) inserted into a sequence so that two sequences can be aligned properly. It represents a biological event: *Insertion* (something added in one sequence) or *Deletion* (something lost in the other).

### Methods

|              | Needleman–Wunsch         | Smith–Waterman  | BLAST                       |
| ------------ | ------------------------ | --------------- | --------------------------- |
| Type         | Global alignment         | Local alignment | Local (heuristic) alignment |
| Accuracy     | Exact                    | Exact           | Approximate                 |
| Speed        | Slow                     | Very slow       | Fast                        |
| Use case     | Full sequence comparison | Motifs/domains  | Database search             |
| Gap handling | Often affine             | Often affine    | Simplified                  |
| Tools        | EMBOSS Needle            | EMBOSS Smith    | BLAST (NCBI BLAST)          |

### Limitations and challenges
- algorithm complexity
- scoring system selection: Alignment quality depends heavily on the scoring scheme
- gap penalties: Difficult to correctly model gaps representing biological insertions/deletions
- sequence length: Sequence length affects both computation and biological interpretability

## Multiple Sequence Alignment
= Aligning 3 or more biological sequences (DNA, RNA, or proteins) simultaneously to identify:
- Conserved regions
- Functional motifs
- Evolutionary relationships
### Main types
- **Global alignment**: align entire sequences end-to-end
- **Local/Motif-focused alignment**: find best matching subsequences

### Methods
|                  | Progressive                                              | Iterative                                           | Consistency-based                     | HMM/Profile                       |
| ---------------- | -------------------------------------------------------- | --------------------------------------------------- | ------------------------------------- | --------------------------------- |
| **How it works** | build pairwise distances -> align sequences step-by-step | start with initial alignment-> repeatedly refine it | combines multiple pairwise alignments | use probabilistic models          |
| **Accuracy**     | Medium                                                   | High                                                | Very high                             | Very high (for families)          |
| **Speed**        | Fast                                                     | Medium                                              | Slow                                  | Medium                            |
| **Use case**     | General-purpose MSA                                      | Higher accuracy alignment                           | Difficult/divergent sequences         | Protein families, remote homology |
| **Tools**        | Clustal Omega, ClustalW                                  | MUSCLE, MAFFT                                       | T-Coffee                              | HMMER                             |
### Limitations and challenges
- computational complexity
- erorr propagation
- sensitivity to parameters

## Structural Alignment
= Aligning based on the 3D structure of biological molecules

## Homology Searching
= Finding sequences in a database that are evolutionarily related to a query sequence
>[!Note] Important distinction
> - Similarity = measurable (alignment score)
> - Homology = biological conclusion (shared ancestry)

# Functional Genomics
## Gene prediction

## Genome annotation and visualization

## Gene functional  analysis

# Omics Data Analysis
see [[LearningNotes/Omics Data Analysis\|Omics Data Analysis]]


