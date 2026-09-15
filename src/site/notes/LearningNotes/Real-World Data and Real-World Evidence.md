---
{"topic":"AIxHealth","dg-publish":true,"permalink":"/LearningNotes/Real-World Data and Real-World Evidence/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"AIxHealth"}}
---

>[!abstract] Summary




>[!info] Related Notes

## What is RWD and RWE
>[!Tip] Source: https://www.fda.gov/science-research/science-and-research-special-topics/real-world-evidence
### Real-world data (RWD)
= data are data relating to patient health status and/or the delivery of health care routinely collected from a variety of sources
- examples
	- electronic health records
	- medical claims
	- disease registry
	- wearables & mobile health
### Real-world evidence (RWE)
= clinical evidence about the usage and potential benefits or risks of a medical product derived from analysis of RWD
- examples
	- safety (e.g. of a drug)
	- (comparative) effectiveness
	- long-term outcome
	- rare adverse events

## Why "real-world" matters
real-world data is more realistic and less controlled than Randomized Clinical Trial (RCT) data
- RCT data are collected under a predefined protocol with controlled measurements and often randomized treatment assignment.
- RWD are generated in routine healthcare, so they are usually: *less standardized, more heterogeneous, more incomplete, more representative of routine clinical practice*

## Key Methodological Concepts

### Fit-for-Purpose Data
A dataset must be appropriate for the specific research question.
### Coding and Phenotype Validity
Clinical concepts are often inferred from codes or combinations of records.
### Missingness and Measurement Error
Missingness in RWD is often **informative**.
### Healthcare-Utilization Bias
Patients who are sicker or have better healthcare access are often observed more frequently -> may partly reflect healthcare utilization rather than underlying disease biology.
### Confounding
Most RWD studies are observational, so treatment or exposure is usually not randomly assigned.

### Data Harmonization
Different datasets may represent the same concept differently.
Harmonization may require:
- unit conversion
- variable mapping
- coding standardization
- common phenotype definitions
- temporal alignment
### Transportability and Generalizability
- Results from one dataset may not hold in another population or healthcare system.
- External validation is therefore important for both clinical prediction models and RWE studies.

## From RWD to RWE

A useful framework is:
```
Research question
        ↓
Fit-for-purpose data
        ↓
Valid variables and phenotypes
        ↓
Assess missingness and measurement
        ↓
Address bias and confounding
        ↓
Appropriate analysis
        ↓
External validation / transportability
        ↓
Credible RWE
```

The key principle is:

> **RWE quality depends on the full study design and data-generation process, not simply on dataset size or statistical model performance.**