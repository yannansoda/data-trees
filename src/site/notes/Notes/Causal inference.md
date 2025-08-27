---
{"topic":"Statistics, Modeling","dg-publish":true,"permalink":"/Notes/Causal inference/","dgPassFrontmatter":true,"noteIcon":""}
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
### Average Treatment Effect (ATE)
- = the average difference in outcomes between if everyone was treated with A=1 and if everyone was treated with A=0:
- formula: 
$$
 E(Y^1 - Y^0)
 $$
 - note that it is different from conditioning (which compares subpopulation)
 $$
 E(Y^1 - Y^0) \neq E(Y|A=1) - E(Y|A=0)
 $$
### Average Treatment Effect on the Treated (ATT)
- = the average causal effect specifically for the group of individuals who actually received the treatment
### Causal relative risk
- formula: 	$$
 E(Y^1 / Y^0)
 $$
### Heterogeneous Treatment Effect (HTE) 
= the phenomenon where the effect of a treatment or intervention varies across individuals or subgroups
#### Conditional Average Treatment Effect (CATE)
- = formalization of HTE = the average treatment effect conditional on a set of covariates or specific subgroups
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

## Causal Graphs
[[Notes/Probabilistic Graphical Models#Directed acyclic graph\|Probabilistic Graphical Models#Directed acyclic graph]]

# Classic Causal Inference Methods
### Controlled Regression/Regression Adjustment
= Isolating the effect of a treatment while adjusting for confounders.
-  Assumes: ignorability (no unmeasured confounding), correct model specification, common support/overlap in covariate distributions
#### How it works
- Fit a regression model, and a coefficient captures the average effect of the corresponding covariate, controlling for other covariates.

### Propensity Score Matching (PSM)
= using statistical techniques to construct an artificial control group by matching each treated unit with a non-treated unit of similar characteristics
- Propensity score = the probability of each participant being in the group A or B
	- e.g. group A is with treatment, group B is without treatment
- Assumes: ignorability (no unmeasured confounding)
#### How it works
It is basically a logistic regression using the control covariates
1. calculate the propensity score of 
	- the disease/treatment group based on the control variables
	- the control group based on the control variables
2. match individuals from the control group to those in the disease group with similar scores using [[Notes/K-Nearest Neighbor\|K-Nearest Neighbor]]
3. after matching: check the covariate balance between the matched treated and control groups
4. estimate treatment effect
#### Why PSM is useful
- it can help create matched groups
- it can help avoid confounds
- it can provide robust solution for estimating causal effects in observational studies
### Instrumental Variables (IV)
= estimating causal effects when there is unmeasured confounding or endogeneity, which addresses:
- endogeneity (when treatment is correlated with unobserved confounders) 
- situations where controlled experiments are not feasible
- extension: [[Notes/Mendelian Randomization\|Mendelian Randomization]]
#### How it works
- Use a variable $Z$ (instrument) that:
	- is correlated with treatment $X$
	- affects the outcome $Y$ only through $X$ (= $Z$ should not suffer from the same endogeneity issues as $X$)
- Two-stage process:
	1. predict $X$ from $Z$
	2. use predicted $\hat{X}$ to estimate effect on $Y$
>[!Example]
>Using the tax rate for tobacco products (Z) as an instrument to estimate the effect of smoking (X) on general health (Y).

### Difference-in-Difference (DiD)
= tracking changes over time: compare changes in outcomes between treated and control groups before and after a treatment
#### How it works
- Compare before-after differences between groups
- Assumes *parallel trends*: without treatment, treated and control groups would evolve similarly

### Regression Discontinuity Design (RDD)
= Exploiting a known **threshold rule** to mimic randomization.
#### How it works
- Units just above and below a cutoff are assumed to be comparable
# Machine Learning Approaches for Causal Inference (Causal ML)
= Using machine learning to estimate causal effects more flexibly
- Causal ML: estimate HTE ([[Notes/Causal inference#Heterogeneous Treatment Effect (HTE)\|Causal inference#Heterogeneous Treatment Effect (HTE)]])
- classic causal inference methods: primarily estimate ATE ([[Notes/Causal inference#Average Treatment Effect (ATE)\|Causal inference#Average Treatment Effect (ATE)]])
### Causal Forests
= [[Notes/Decision Tree & Random Forest#Random Forest\|Decision Tree & Random Forest#Random Forest]] algorithm adapted to estimate [[Notes/Causal inference#Conditional Average Treatment Effect (CATE)\|Causal inference#Conditional Average Treatment Effect (CATE)]]
#### How it works
- different from standard Random Forests that minimize prediction error, Causal Forests construct trees by splitting data to maximize the difference in the relationship between an outcome variable and a "treatment" variable across the resulting splits
-  the data is split into two subsets
	- one subset is used for determining the tree splits (structure learning)
	- the other is used for estimating the treatment effects within the terminal nodes (estimation)
### Double Machine Learning (DML)
= debiased or orthogonal ML
- goal of DML: provide valid confidence intervals and achieve "root-n-consistent" estimation, meaning the estimation error decreases efficiently as the sample size increases
- rooted in the Frisch-Waugh-Lovell (FWL) theorem
### Meta-Learners (S-learner, T-learner, X-learner)
#### S-learner (Single Learner)
Include treatment as a feature in one model
#### T-learner (Two Learners)
Train separate models for treated and control groups.
#### X-learner (Extended Learner)
Improves efficiency for imbalanced treatment groups.




