---
{"topic":"Statistics, Modeling","dg-publish":true,"permalink":"/LearningNotes/Linear Mixed Models/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"Statistics, Modeling"}}
---

# First, What does mixed-effects mean
## Mixed-effects models
- A **mixed-effects model** is a statistical model that **mixes** both:
	- **fixed effects**: population-level effects *(effects we want to estimate directly)*
	- **random effects**: group-level or individual-level deviations *(variability caused by sampling)*
- Useful when data are not fully independent, but the dependency has a meaningful structure
	- example: repeated measurements from the same subject ([[LearningNotes/Longitudinal Data Analysis\|Longitudinal Data Analysis]])
	- example: students nested within schools
	- example: patients nested within hospitals
- The core idea: model the **average pattern** while also accounting for **individual / group differences**

## Fixed effects vs. random effects
### Fixed effects
- Fixed effects answer: **what is the average relationship in the population?**
- Example:
	- if we study the effect of treatment, the treatment effect is usually a fixed effect
	- it represents the average treatment effect across the whole population
### Random effects
- Random effects answer: **how much do individuals or groups deviate from that average?**
- Example:
	- each subject may have a different baseline level / average performance
	- each patient may respond differently to time

# Linear mixed model (LMM)
## What is LMM
- **Linear mixed model (LMM)**, also called **linear mixed-effects model**:
	- a type of [[LearningNotes/Linear Mixed Models#Mixed-effects models\|mixed-effects model]] for continuous outcomes *(but not all mixed-effects models are LMMs; see [[LearningNotes/Generalized Linear Models\|Generalized Linear Models]])*
	- "Linear": the response is modeled as a linear combination of predictors, similar to [[LearningNotes/Regression\|Regression]]
- LMM is useful when the data have both:
	- **within-group variability**: e.g., repeated measurements from the same subject
	- **between-group variability**: e.g., differences between subjects, hospitals, schools, batches, etc.

>[!tip] LMM vs. GLMM
>- **LMM** is mainly for continuous outcomes that are approximately normally distributed.
>- For binary, count, ordinal, or categorical outcomes, use a **generalized linear mixed model (GLMM)** instead.

## Formula
$$Y = X\beta + Zb + \epsilon$$
- $Y$: response vector
- $X$: design matrix for fixed effects
- $\beta$: fixed-effect coefficients
- $Z$: design matrix for random effects
- $b$: random-effect coefficients
- $\epsilon$: residual error

>[!tip] Compared to [[LearningNotes/ANOVA & Post-hoc Tests\|ANOVA & Post-hoc Tests]], a basic ANOVA model does not include the random-effect term:
$$Y = X\beta + \epsilon$$

### Intuition of the formula
- $X\beta$ = population-level average pattern
- $Zb$ = subject-level / group-level deviation from the average pattern
- $\epsilon$ = leftover noise not explained by the model

## Why LMM matters
### Compared to ANOVA
Compared to [[LearningNotes/ANOVA & Post-hoc Tests\|ANOVA & Post-hoc Tests]], LMM is more flexible:
- It can handle **non-independent observations**, such as repeated measures ([[LearningNotes/Longitudinal Data Analysis\|Longitudinal Data Analysis]]) or clustered data
- It can model correlation within the same subject or group
- It can handle **unbalanced data**, where different groups have different numbers of observations
- It can often handle missing observations better than repeated-measures ANOVA, as long as the missingness assumption is reasonable

### When to use LMM
Use LMM when:
- the outcome is continuous
- observations are correlated within subject / group / cluster
- each subject or group can have its own baseline level or slope
- the data are hierarchical, nested, longitudinal, or repeated-measures
## Assumptions for using LMM
### Sampling and independence
- Subjects or groups are sampled from the population of interest.
- Observations from different individuals / groups are independent.
- Repeated measurements from the same individual are **not assumed to be independent**; this dependence is modeled through random effects and/or covariance structure.
### Distribution assumptions
- Conditional on the fixed and random effects, residuals are approximately normally distributed.
- Random effects are usually assumed to be normally distributed.
- Missing data are assumed to be ignorable, often interpreted as [[LearningNotes/Handling Missing Data#^656f1e\|missing at random (MAR)]].
### Covariance structure
- see [[LearningNotes/Covariance Structure\|Covariance Structure]]
## How to build an LMM
1. **Decide fixed effects**
2. **Decide random effects**
	- Random intercepts/slopes only? intercepts + random slopes?
	- Which grouping variable should have random effects?
3. **Decide [[LearningNotes/Covariance Structure\|Covariance Structure]]**
	- Which structure best describes within-subject or within-group correlation?
4. **Decide common model structures**
	- random intercept only
	- random intercepts + fixed slopes
	- fixed intercepts + random slopes
	- random intercepts + random slopes
5. **Compare candidate models**
	- Use [[LearningNotes/Likelihood ratio test\|likelihood ratio tests]], AIC / BIC, or [[LearningNotes/Cross-Validation\|cross-validation]]
	- Prefer the model that is interpretable and fits the dependency structure well; covariance parameters are often estimated using [[LearningNotes/Maximum likelihood estimation\|Maximum likelihood estimation]] or related methods
	- Avoid making the random-effects structure too complex if the data cannot support it