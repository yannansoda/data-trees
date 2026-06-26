---
{"topic":"Statistics, Modeling","dg-publish":true,"permalink":"/LearningNotes/Structural Equation Models/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"Statistics, Modeling"}}
---

# What is SEM
**Structural equation modeling (SEM)** = a framework for modeling relationships among **observed** and **latent** variables.

- combines ideas from:
	- [[LearningNotes/Regression\|Regression]]
	- factor analysis
	- path analysis
- can estimate several related equations simultaneously
- is usually confirmatory: the researcher specifies a model, then evaluates how well it fits the data

## Key Components

### Observed Variables
= variables measured directly, e.g. blood pressure, biomarker levels, questionnaire items

### Latent Variables
= unobserved constructs inferred from multiple indicators, e.g. frailty, depression, socioeconomic status

### Measurement Model
= defines how *observed* indicators measure *latent* variables

- closely related to confirmatory factor analysis
- example: fatigue, weakness, and low activity measure latent **frailty**

### Structural Model
= defines relationships among observed or latent variables

- similar to a system of regression equations
- can include direct, indirect, and mediated associations

> [!Important]
> SEM arrows encode specified directional relationships, but they do not establish causality without appropriate study design and assumptions. See [[LearningNotes/Causal inference\|Causal inference]] and [[LearningNotes/Probabilistic Graphical Models\|Probabilistic Graphical Models]].

# When to Use SEM
- measure a construct using several imperfect indicators
- test direct and indirect pathways
- model multiple dependent variables jointly
- account explicitly for measurement error
- compare a theoretical model with observed covariance patterns
- model longitudinal change using [[LearningNotes/Structural Equation Models#Latent Growth Curve Models\|#Latent Growth Curve Models]]

# Latent Growth Curve Models
= longitudinal SEMs that represent change over time using latent growth factors

- **intercept factor** = initial level
- **slope factor** = rate of change
- variation in the factors represents individual differences in baseline and change
- predictors can explain differences in intercepts or slopes

Health example:
> Model baseline cognition and rate of cognitive decline from repeated cognitive-test scores, then test whether APOE-e4 predicts faster decline.

# Advantages
- models latent variables and measurement error
- estimates multiple pathways simultaneously
- tests mediation and indirect effects
- supports longitudinal and multigroup models

# Limitations
- requires strong model specification
- often needs a large sample
- estimates can be sensitive to non-normality and missing data
- different models may fit the same covariance structure
- good model fit does not prove that the model is correct

# Model Fit

Common fit measures:
- **Chi-square test**: tests exact fit; sensitive to sample size
- **CFI/TLI**: compare the specified model with a baseline model
- **RMSEA**: estimates approximate lack of fit
- **SRMR**: average standardized residual

> [!Tip]
> Do not select a model from one cutoff alone. Consider theory, parameter estimates, residuals, and several fit indices together.

# Practical Workflow
1. Define the theoretical model.
2. Identify observed and latent variables.
3. Specify the measurement and structural models.
4. Check identification and sample size.
5. Fit the model.
6. Review fit indices, residuals, and parameter estimates.
7. Modify only when theoretically justified.
8. Validate the model in new data when possible.
