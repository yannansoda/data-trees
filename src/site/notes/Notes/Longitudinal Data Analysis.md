---
{"topic":"DataScience","dg-publish":true,"permalink":"/Notes/Longitudinal Data Analysis/","dgPassFrontmatter":true,"noteIcon":""}
---

## Definitions

## Data Structure
- 'long' format: one row. for each time point by subject combination
- 'wide' format: one row per subject
## Properties
- repeated observations are usually correlated
- robust to missing data and irregularly spaced measurement occasions (only if Mixed effect modeling was used)

## Modeling strategies
### Traditional methods
- ANCOVA (adjusting for baseline differences)
- Repeated-measures ANOVA (univariate approach)
- MANOVA (multivariate approach)
### Newer methods
- Generalized Estimating Equations (GEE) Models
- Structural Equations Models
	- used for modeling the relationships among observed and latent variables based on a set of specified structural equations
	- a multivariate statistical method that combines aspects of factor analysis and multiple regression analysis
- Transition Models
- Mixed-effects Models