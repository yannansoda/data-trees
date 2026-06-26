---
{"topic":"Math, Modeling","dg-publish":true,"permalink":"/LearningNotes/Generalized Linear Models/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"Math, Modeling"}}
---

# Overview

A **generalized linear model (GLM)** extends ordinary [[LearningNotes/Regression#Linear Regression\|linear regression]] so that the outcome can be **continuous, binary, count, or another exponential-family outcome**.

> [!summary] Core idea
> A GLM models the expected outcome through a **link function** applied to a linear predictor:
> $$
> g(\mathbb{E}[Y_i]) = \eta_i = \alpha + \beta_1X_{i1} + \beta_2X_{i2} + \cdots
> $$
> where $g(\cdot)$ is the link function and $\eta_i$ is the linear predictor.

## Three Components

1. **Random component**: the outcome distribution, e.g. Normal, Bernoulli, Poisson.
2. **Systematic component**: the linear predictor $\eta = X\beta$.
3. **Link function**: maps the expected outcome to the linear predictor scale.

In other words, a GLM combines:

- a **linear predictor**: $X\beta$
- a **link function / nonlinearity**: $g(\mu)$
- a **noise model / outcome distribution**: $Y \sim$ chosen family

# Common GLM Examples

| Model | Outcome type | Distribution | Link function | Typical question |
|---|---|---|---|---|
| Linear regression ([[LearningNotes/Regression#Linear Regression\|Regression#Linear Regression]]) | Continuous | Normal | Identity | How does $Y$ change with $X$? |
| Logistic regression ([[LearningNotes/Regression#Logistic Regression\|Regression#Logistic Regression]]) | Binary | Bernoulli | Logit | How does $X$ affect the probability of an event? |
| Poisson regression | Count | Poisson | Log | How does $X$ affect an event rate or count? |

### Linear Regression as a GLM

$$
Y_i \sim \text{Normal}(\mu_i, \sigma)
$$

$$
\mu_i = \alpha + \beta_X X_i + \beta_Z Z_i
$$

- Link: identity
- Interpretation: coefficients are additive changes in the expected value of $Y$.

### Logistic Regression as a GLM

$$
Y_i \sim \text{Bernoulli}(p_i)
$$

$$
\text{logit}(p_i) = \log\left(\frac{p_i}{1-p_i}\right) = \alpha + \beta_X X_i + \beta_Z Z_i
$$

- Link: logit
- Interpretation: coefficients are changes in **log-odds**; exponentiated coefficients are [[LearningNotes/Regression#Logistic Regression\|odds ratios]].

### Poisson Regression as a GLM

$$
Y_i \sim \text{Poisson}(\lambda_i)
$$

$$
\log(\lambda_i) = \alpha + \beta_X X_i + \beta_Z Z_i
$$

Equivalently:

$$
\lambda_i = \exp(\alpha + \beta_X X_i + \beta_Z Z_i)
$$

- Link: log
- Interpretation: coefficients are changes in the log expected count; exponentiated coefficients are rate ratios.

# Relationship to Other Models
## Relationship to Mixed Models

GLMs assume that observations are independent unless the model is extended. This is where [[LearningNotes/Linear Mixed Models\|Linear Mixed Models]] and generalized mixed models become important.

> [!tip] GLM, LMM, and GLMM
> - **GLM** = generalized outcome distribution + link function, but usually independent observations.
> - **[[LearningNotes/Linear Mixed Models\|LMM]]** = linear/Normal outcome model + random effects for clustered or repeated data.
> - **GLMM** = GLM + random effects; useful for binary/count repeated-measures or clustered outcomes.

Example:
- Binary outcome, independent patients → logistic regression GLM.
- Continuous repeated measurements → [[LearningNotes/Linear Mixed Models\|LMM]].
- Binary repeated measurements from the same patients → logistic GLMM.

## Relationship to GEE

**Generalized estimating equations (GEE)** extend the GLM idea to **correlated observations**, such as repeated measurements from the same patient in [[LearningNotes/Longitudinal Data Analysis\|Longitudinal Data Analysis]].

| Feature | GLM | GEE |
|---|---|---|
| Data | Independent observations | Correlated or repeated observations |
| Target | Covariate–outcome association | Population-average association |
| Outcomes | Continuous, binary, count, etc. | Same outcome families via link functions |
| Correlation | Usually assumes independence | Specifies a working within-subject correlation |
| Interpretation | Model-specific mean association | Marginal / population-average association |

GEE is closely related to GLMs, but it is **not simply another GLM distribution**. It is an estimation framework for correlated data.

## Related Notes

- [[LearningNotes/Regression\|Regression]] — linear and logistic regression foundations
- [[LearningNotes/Linear Mixed Models\|Linear Mixed Models]] — mixed-effects models for continuous repeated or clustered outcomes
- [[LearningNotes/Longitudinal Data Analysis\|Longitudinal Data Analysis]] — choosing among LMM, GEE, and other longitudinal methods
- [[LearningNotes/ANOVA & Post-hoc Tests\|ANOVA & Post-hoc Tests]] — classical linear-model comparisons
- [[LearningNotes/Random Variables & Probability distributions\|Random Variables & Probability distributions]] — distributions used as GLM outcome families
