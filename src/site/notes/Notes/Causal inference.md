---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Causal inference/","dgPassFrontmatter":true,"noteIcon":""}
---

# Basics
## What is Causal inference 
- is prediction of intervention: What if I do this?
- is imputation of missing observations: What if I had done something else?
### Counterfactuals
The fundamental problem of causal inference is we only observe one treatment and one outcome for each person.
- A counterfactual is a hypothetical scenario used to reason about what *would* have happened if a different action or condition had been present. 
- It’s fundamental in defining causal effects.
- Often confused with:
	- **potential outcomes framework** defines causal effects by comparing what would happen under different treatments or conditions
	- **counterfactual outcome**: the potential outcome not observed due to the actual treatment
## Causal Effects
#### Average Treatment Effect (ATE)
- = the average difference in outcomes between if everyone was treated with A=1 and if everyone was treated with A=0:
- formula: 
$$
 E(Y^1 - Y^0)
 $$
 - note that it is different from conditioning (which compares subpopulation)
 $$
 E(Y^1 - Y^0) \neq E(Y|A=1) - E(Y|A=0)
 $$
#### Average Treatment Effect on the Treated (ATT)
- = the average causal effect specifically for the group of individuals who actually received the treatment
#### Causal relative risk**
- formula: 	$$
 E(Y^1 / Y^0)
 $$
#### Conditional Average Treatment Effect (CATE)
- = the average treatment effect conditional on a set of covariates or specific subgroups
- formula: $$
E(Y^1 - Y^0 | V=v)
$$
## Core Assumptions for Causal Identification
- = the foundational beliefs or conditions necessary to establish valid causal inferences from data
### Stable Unit Treatment Value Assumption (SUTVA)
This assumption comprises these critical components:
- **no interference (spillover/contagion)**: the treatment assigned to one individual does not affect the potential outcomes of another individual
- **no hidden variations**: there is only one version of each treatment level
- **treatment consistency**: the potential outcomes for an individual under a given treatment are exactly what would be observed if that treatment were actually applied
### Ignorability (or Unconfoundedness/No Unmeasured Confounding)
- given pre-treatment covariates X, treatment assignment is independent from the potential outcomes
### Positivity (or Common Support/Overlap)
- assumes that for every combination of confounders, there is a non-zero probability of receiving each treatment level
- this means that there must be sufficient variation in treatment assignment across all levels of the confounding variables

## Bias in Causal Studies
### Confounding Bias
- occurs when an observed association between an exposure and an outcome is distorted by the effect of an uncontrolled common cause
- confounder = a variable that satisfies three criteria
	- it is predictive of the outcome (even in the absence of the treatment)
	- it is associated with the treatment
	- it is not an intermediate variable in the causal pathway between the treatment and the outcome
- Example: Age might affect both treatment assignment and recovery rate.
### Selection Bias (Collider Bias)
- occurs when the process of selecting individuals into a study (or into observed data) is influenced by both the exposure and the outcome, or by variables correlated with them.
- it's often a form of **collider bias"
- collider = a variable that is itself caused by two other variables

### Measurement Bias

# Classic Causal Inference Methods

# Machine Learning Approaches for Causal Inference (Causal ML)


# Core Methods 
### Controlled Regression
= Isolating the effect of a treatment while adjusting for confounders.
#### How it works
- Fit a regression model, and a coefficient captures the average effect of the corresponding covariate, controlling for other covariates.
- Assumes ignorability and linearity
### Regression Discontinuity Design (RDD)
= Exploiting a known **threshold rule** to mimic randomization.
#### How it works
- Units just above and below a cutoff are assumed to be comparable
### Difference-in-Difference (DiD)
= tracking changes over time: compare changes in outcomes between treated and control groups before and after a treatment
#### How it works
- Compare before-after differences between groups
- Assumes parallel trends: without treatment, treated and control groups would evolve similarly
### Instrumental Variables (IV)
= Addressing endogeneity (when treatment is correlated with unobserved confounders).
#### How it works
- Use a variable $Z$ (instrument) that:
	- is correlated with treatment $A$
	- affects the outcome $Y$ only through $A$
- Two-stage process:
	1. predict $A$ from $Z$
	2. use predicted $\hat{A}$ to estimate effect on $Y$
### ML + Causal Inference
= Using machine learning to estimate causal effects more flexibly, especially for **heterogeneous treatment effects (HTEs)**.
#### How it works
Common strategies:
- **T-Learner**: Train separate models for treated and control groups.
- **S-Learner**: Include treatment as a feature in one model.
- **X-Learner**: Improves efficiency for imbalanced treatment groups.
- **Double ML / DML**: Debias treatment effect estimates using ML residuals.

## Causal Graphs
[[Notes/Probabilistic Graphical Model#Directed acyclic graph\|Probabilistic Graphical Model#Directed acyclic graph]]

## Confounds in causal inference
### The Four Elemental Confounds
{ #b7b0a6}


![4-elemental-confounds.png|300](/img/user/_assets/images/4-elemental-confounds.png)

| Confound type  | Description                                       | Take care...                                      |     |     |
| -------------- | ------------------------------------------------- | ------------------------------------------------- | --- | --- |
| The Fork       | X and Y are associated unless stratified by Z     | -                                                 |     |     |
| The Pipe       | X and Y are associated unless stratified by Z     | post-treatment bias                               |     |     |
| The Collider   | X and Y are not associated unless stratified by Z | collider bias                                     |     |     |
| The Descendant | X and Y are causally associated through Z         | once stratified by A, X and Y are less associated | -   |     |
|                |                                                   |                                                   |     |     |




