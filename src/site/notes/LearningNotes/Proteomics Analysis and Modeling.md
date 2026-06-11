---
{"topic":"AIxHealth","dg-publish":true,"permalink":"/LearningNotes/Proteomics Analysis and Modeling/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"AIxHealth"}}
---

# What is proteomics?

- **Proteomics** = the large-scale study of proteins, including which proteins are present, how abundant they are, and how they vary across biological or clinical states.
- Compared with genomics
	- The genome is mostly stable, but the proteome changes with disease, age, environment, medication, inflammation, and tissue activity.
- Proteomics is usually close to the current physiological state of a person, tissue, or sample.
	- useful for biomarker discovery, disease stratification, risk prediction, and biological interpretation. 
	- most useful when the biology involves active processes:
		- immune activation
		- tissue injury
		- metabolic dysregulation
		- coagulation
		- cardiovascular stress
		- organ dysfunction
		- drug response

# Common proteomics platforms

## Mass spectrometry

- **Mass spectrometry-based proteomics** identifies and quantifies proteins or peptides using mass-to-charge signals.
- It is powerful for discovery because it does not require a predefined antibody or aptamer panel.
- Typical output values include intensities, LFQ intensities, spectral counts, or abundance ratios.
- Common issues:
	- many missing values, especially for low-abundance proteins
	- batch and run-level technical variation
	- peptide-to-protein mapping ambiguity
	- more complex preprocessing than many panel-based platforms
- Strengths:
	- discovery-oriented
	- can support peptide-level analysis
	- can sometimes support isoform or post-translational modification analysis

## Olink

- **Olink** uses proximity extension assay technology and is common in plasma proteomics.
- The usual output is **NPX** = Normalized Protein eXpression.
- NPX is usually log2-scaled and relative, not an absolute clinical concentration.
- Olink datasets often include plate, batch, panel, limit of detection, missingness, and QC metadata.
- It is well suited for population-scale association studies, biomarker discovery, and risk modeling.

## SomaScan

- **SomaScan** uses modified aptamers to measure proteins at high throughput.
- The output is often RFU or normalized RFU-like values.
- SomaScan can measure thousands of proteins and is common in large plasma proteomics studies.
- Main things to check:
	- platform-specific normalization
	- assay-to-protein mapping
	- whether values are comparable across batches or studies
	- how missingness and QC flags are represented
# Data characteristics & Challenges
## What proteomics data looks like
- Most downstream analysis starts with a sample-by-feature matrix.
- Rows are samples and columns are metadata, phenotypes, covariates, and protein features.

| sample_id | age | sex | BMI  | disease_status | batch | protein_A | protein_B | protein_C |
| --------- | --- | --- | ---- | -------------- | ----- | --------- | --------- | --------- |
| S001      | 63  | F   | 28.4 | 0              | B1    | 5.23      | 8.91      | NA        |
|S002      | 71  | M   | 31.2 | 1              | B1    | 4.82      | 9.10      | 6.34
|S003      | 56  | F   | 24.9 | 0              | B2    | 5.44      | 8.72      | 6.01

- Typical metadata columns:
	- sample ID
	- age, sex, BMI, disease status, clinical scores
	- smoking, medication, ancestry, site
	- batch, plate, run date, assay panel
	- sample QC and protein QC flags
- Typical protein columns:
	- one column per measured protein or assay
	- values are usually relative abundance measurements
	- identifiers may be assay IDs, gene symbols, UniProt IDs, or platform-specific IDs
## Key data characteristics
### Relative abundance
- Most proteomics values are relative abundance measures, not direct clinical concentrations.
- They are useful for comparing samples within the same processed dataset.
- Interpretation should respect the platform and normalization method.
### High dimensionality
- Proteomics datasets often contain hundreds to thousands of protein features.
- Smaller studies may have fewer samples than proteins.
- This creates risks of overfitting, false discovery, and unstable biomarker rankings.
### Correlated features
- Proteins are often correlated because they share pathways, tissue sources, immune programs, or technical effects.
- Correlation can make model coefficients unstable.
- It can also make feature importance hard to interpret.
### Batch effects
- Proteomics measurements can vary by plate, batch, collection site, run order, instrument, storage time, or sample processing.
- Batch effects can be stronger than the biological signal.
- Batch structure should be checked before modeling, usually with PCA or UMAP colored by technical variables.
### Non-random missingness ([[LearningNotes/Handling Missing Data#^b7a197\|Handling Missing Data#^b7a197]])
- Missing values are often informative in proteomics.
- A protein may be missing because it is below the detection limit, failed QC, or was not measured in a subset of samples.
- Missingness can reflect biology, technical failure, or both.

## Main preprocessing challenges
### Missing values
- Missingness is one of the most important issues in proteomics analysis.
- Common strategies ([[LearningNotes/Handling Missing Data#How to handle missing data\|Handling Missing Data#How to handle missing data]])
	- Deletion
		- remove proteins with high missingness
		- remove samples with high missingness
	- Imputation
		- use median or simple imputation for low missingness
		- use KNN, MICE, random forest, or model-based imputation when justified
		- use left-censored imputation for some mass spectrometry settings
	- add missingness indicators if missingness itself may be informative
- Good practice:
	- inspect missingness by sample, protein, batch, and outcome
	- avoid fitting imputation methods on the full dataset before validation
	- report missingness thresholds clearly
### Batch effects
- Batch effects can create false biomarker signals.
- Common checks:
	- [[LearningNotes/Dimensionality Reduction\|Dimensionality Reduction]]: PCA or UMAP colored by batch, plate, site, and outcome
	- protein distributions by batch
	- missingness rates by batch
	- association between batch and phenotype
- Common strategies:
	- include batch or plate as covariates
	- normalize within appropriate technical groups
	- use ComBat or similar methods when justified
	- use blocked or stratified splitting if batch structure affects validation
- Important caution: if batch and outcome are confounded, batch correction can behave unpredictably.
### Scaling and transformation
- Many datasets are already normalized or log-transformed by the data provider.
- Always check the measurement scale before transforming again.
- Standardization is usually needed before:
	- elastic net
	- ridge or lasso regression
	- PCA
	- distance-based methods
	- neural networks
- In predictive modeling, scaling parameters should be fitted on the training set only.
### Outliers ([[LearningNotes/Outlier & Anomaly Detection\|Outlier & Anomaly Detection]])
- Outliers can be technical artifacts or true biological extremes.
- Common checks:
	- sample-level median intensity
	- total signal
	- number of missing proteins per sample
	- PCA leverage points
	- protein-level extreme values
	- assay QC flags
- Outliers should not be removed automatically; the reason should be investigated and documented.
### Multiple testing
- Testing thousands of proteins creates many false positives.
- Common approaches:
	- Benjamini-Hochberg FDR correction ([[LearningNotes/Adjusting p-values in Statistical analysis\|Adjusting p-values in Statistical analysis]])
	- q-values
	- replication in another cohort
	- cross-validation-based stability checks
	- external validation when available
# Common analysis workflow
## 1. Define the target
- Start by defining the biological or clinical question.
- The target determines the model, evaluation metric, and validation design.
- Common target types:
	- continuous outcome: age, BMI, HbA1c, blood pressure, risk score
	- binary outcome: case/control, disease status, treatment response
	- multiclass outcome: subtype or severity category
	- time-to-event outcome: incident disease, progression, mortality
	- unsupervised goal: sample clustering or molecular subtype discovery
## 2. Prepare metadata and covariates
- Covariates matter because many proteins vary with demographic, clinical, and technical factors.
- Common covariates:
	- age
	- sex
	- BMI
	- smoking
	- medication use
	- ancestry or genetic principal components
	- clinical site
	- batch, plate, run date, instrument
	- sample storage time or collection time
- Without covariate adjustment, a protein may look disease-associated only because it is correlated with age, sex, BMI, or batch.
## 3. Quality control
- Typical QC steps:
	- check sample counts and duplicated IDs
	- check phenotype missingness
	- check protein missingness
	- check assay QC flags
	- visualize protein distributions
	- visualize batch structure
	- filter low-quality samples and proteins
	- choose imputation, scaling, and transformation strategies
- QC decisions should be documented because they shape all downstream results.
## 4. Exploratory data analysis

- Useful EDA views:
	- missingness heatmap
	- protein abundance histograms
	- PCA or UMAP colored by batch and phenotype
	- correlation matrix of selected proteins
	- volcano plot for univariate associations
	- boxplots or violin plots for top proteins
	- outcome distributions by demographic group
- EDA helps separate plausible biological signal from technical artifacts.

## 5. Association analysis

- Association analysis asks whether each protein is statistically related to an outcome, usually after covariate adjustment.
- It is often easier to interpret than machine learning feature importance.

```text
continuous_outcome ~ protein + age + sex + BMI + batch
binary_outcome     ~ protein + age + sex + BMI + batch
survival_outcome   ~ protein + age + sex + BMI + batch
```

- Common models:
	- linear regression for continuous outcomes
	- logistic regression for binary outcomes
	- Cox proportional hazards models for time-to-event outcomes
	- mixed-effects models for repeated measures or family structure
- Typical outputs:
	- effect size
	- confidence interval
	- p-value
	- FDR-adjusted q-value
	- direction of association

## 6. Predictive modeling

- Predictive modeling asks how well protein features predict an outcome.
- Prediction is not the same as causal explanation.
- Common models:
	- linear or logistic regression as baselines
	- ridge regression for correlated high-dimensional features
	- lasso for sparse feature selection
	- elastic net for sparse but correlated proteomics features
	- random forest for nonlinear relationships
	- XGBoost or LightGBM for tabular prediction
	- Cox regression or penalized Cox models for survival outcomes
	- survival forests or boosting models for nonlinear survival analysis
- Elastic net is often a good first model for proteomics because it handles high-dimensional correlated features and remains relatively interpretable.

## 7. Feature ranking and biomarker prioritization

- Feature importance should be treated as evidence, not proof.
- Common ranking methods:
	- adjusted regression coefficients
	- elastic net selection frequency across folds
	- stability selection across resamples
	- permutation importance
	- SHAP values for tree-based models
	- univariate association strength
	- replication across datasets
- Stronger biomarker candidates usually have:
	- robust association with the outcome
	- stable selection across resampling
	- contribution to predictive performance
	- biological plausibility
	- acceptable missingness and assay quality
	- replication or external validation

## 8. Biological interpretation

- After identifying candidate proteins, the next step is to understand what biological processes they represent.
- Common resources:
	- UniProt for protein function, gene names, subcellular location, domains, and annotations
	- Gene Ontology for biological process, molecular function, and cellular component
	- Reactome for curated pathways
	- KEGG, WikiPathways, MSigDB, or other pathway collections
	- Human Protein Atlas for tissue expression and localization
- Common analyses:
	- over-representation analysis
	- gene set enrichment analysis
	- pathway enrichment
	- protein-protein interaction networks
	- tissue or cell-type enrichment
	- secreted or membrane protein annotation
- Important detail: the enrichment background should usually be the proteins measured in the dataset, not the entire genome.
## 9. Model evaluation
- Evaluation depends on the outcome type.
- For continuous outcomes:
	- RMSE
	- MAE
	- $R^2$
	- Pearson or Spearman correlation
	- predicted-versus-observed calibration
- For binary outcomes:
	- AUROC
	- PR-AUC
	- sensitivity and specificity
	- balanced accuracy
	- calibration curve
	- Brier score
	- decision curve analysis
- For survival outcomes:
	- C-index
	- time-dependent AUC
	- calibration at fixed time points
	- Kaplan-Meier curves by predicted risk group
	- integrated Brier score ([[LearningNotes/Survival Analysis#Brier Score (time-dependent)\|Survival Analysis#Brier Score (time-dependent)]])
- A proteomics model should usually be compared against a reasonable baseline, such as demographic or clinical covariates alone.
# Common modeling pitfalls

## Data leakage 
- see [[LearningNotes/Data Leakage\|Data Leakage]]
## Overinterpreting feature importance
- A highly ranked protein is not automatically causal.
- It may be important because it is correlated with:
	- a causal protein
	- a technical artifact
	- a demographic variable
	- batch structure
- Feature importance is best interpreted together with association results, stability, biological plausibility, and validation.
## Ignoring covariates
- Many proteins vary strongly by age, sex, BMI, kidney function, medication, inflammation, and batch.
- A model can look biologically meaningful while mostly learning confounding structure.
## Unstable biomarker lists
- High-dimensional correlated data can produce different top proteins across different train-test splits.
- Stability across resampling is often more informative than a single ranked list.
## Wrong enrichment background
- Pathway enrichment requires a background feature universe.
- In proteomics, the background should usually be the measured protein set.
- Using all human genes can inflate or distort enrichment results.
## Confusing prediction with mechanism
- A strong predictive signature is not automatically mechanistic.
- Mechanistic claims need stronger evidence, such as perturbation experiments, longitudinal designs, genetic instruments, or external literature.
# Practical questions before analysis

- What platform generated the data?
- What does one protein value mean on this platform?
- Is the data already normalized or log-transformed?
- What are the sample and protein QC fields?
- How much missingness exists by sample, protein, batch, and outcome?
- Are batch and outcome confounded?
- Which covariates should be adjusted for?
- Is the goal association, prediction, clustering, or mechanism?
- What is the correct validation strategy?
- What is the correct feature universe for enrichment?
- Are protein identifiers mapped to stable gene symbols or UniProt IDs?

# Minimal end-to-end template

```text
1. Load protein matrix and metadata.
2. Merge samples and verify identifiers.
3. Inspect missingness, distributions, outliers, and batch structure.
4. Filter low-quality samples and proteins.
5. Split data into training and validation sets.
6. Fit imputation and scaling on training data only.
7. Run baseline association models with covariates.
8. Train predictive models with cross-validation.
9. Rank proteins using stable, resampling-aware methods.
10. Evaluate model discrimination, calibration, and robustness.
11. Annotate top proteins using UniProt or similar resources.
12. Run pathway enrichment with the measured protein set as background.
13. Summarize findings with limitations and validation status.
```

