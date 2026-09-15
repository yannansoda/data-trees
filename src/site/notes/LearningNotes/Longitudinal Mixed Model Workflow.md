---
{"topic":"Statistics, Modeling","dg-publish":true,"permalink":"/LearningNotes/Longitudinal Mixed Model Workflow/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"Statistics, Modeling"}}
---

# Overview

A longitudinal mixed model workflow is a practical way to build [[LearningNotes/Linear Mixed Model\|linear mixed models]] for repeated measurements over time.

## Core logic
Where is the variation?
-> How does the outcome change over time?
-> How do individuals differ in that change?
-> What explains those differences?


>[!important]
>Build model complexity only when it corresponds to a meaningful scientific question.

## Composite model form

For longitudinal data, level-1 and level-2 models can be combined into one equation.

For a random-intercept + random-slope model:

$$
Y_{ij}
=
\gamma_{00}
+
\gamma_{10}TIME_{ij}
+
\zeta_{0i}
+
\zeta_{1i}TIME_{ij}
+
\epsilon_{ij}
$$

- $\gamma_{00}$: population-average intercept / initial status
- $\gamma_{10}$: population-average rate of change
- $\zeta_{0i}$: individual deviation in intercept
- $\zeta_{1i}$: individual deviation in slope
- $\epsilon_{ij}$: within-person residual

The residual structure naturally induces dependence among repeated measurements from the same person.

# Before modeling

Before fitting models, examine:
- outcome trajectories over time
- within-person vs. between-person variability
- plausible functional form of time
- missingness patterns
- irregular measurement schedules

The goal is to see whether systematic change and meaningful individual heterogeneity are present.

# Model-building strategy

A useful strategy is to build the model gradually:

$$
\text{Unconditional means}
\rightarrow
\text{Unconditional growth}
\rightarrow
\text{Conditional growth}
$$

Each new model is interpreted relative to a simpler baseline.

## 1. Unconditional means model

No TIME or substantive predictors:

$$
Y_{ij}=\gamma_{00}+\zeta_{0i}+\epsilon_{ij}
$$

Purpose:
- estimate the overall mean
- partition variation into:
	- between-person variance
	- within-person variance
- determine whether meaningful outcome variation exists
- provide a baseline for later models

No systematic change over time is modeled yet.

## 2. Unconditional growth model

Add TIME:

$$
Y_{ij}
=
\gamma_{00}
+
\gamma_{10}TIME_{ij}
+
\zeta_{0i}
+
\zeta_{1i}TIME_{ij}
+
\epsilon_{ij}
$$

Purpose:
- estimate the population-average trajectory
- determine whether individuals differ in:
	- initial status
	- rate of change
- assess how much within-person variation is explained by TIME
- estimate the intercept-slope covariance

A significant random-slope variance suggests meaningful heterogeneity in rates of change that may be explained by predictors.

## 3. Conditional growth model

Add substantive predictors based on the research question.

Predictors can be:
- time-invariant predictors
- time-varying predictors

### Time-invariant predictors

A time-invariant predictor has one value for each individual.

Examples:
- sex
- genotype
- baseline age
- treatment group
- education level

Time-invariant predictors can explain individual differences in intercepts and/or slopes.

For example:

$$
\pi_{0i}
=
\gamma_{00}
+
\gamma_{01}X_i
+
\zeta_{0i}
$$

$$
\pi_{1i}
=
\gamma_{10}
+
\gamma_{11}X_i
+
\zeta_{1i}
$$

- $\gamma_{01}$: effect of $X_i$ on initial status
- $\gamma_{11}$: effect of $X_i$ on rate of change

To explain differences in rates of change, include an interaction with TIME.

### Time-varying predictors

A time-varying predictor can take different values for the same individual at different measurement occasions.

Examples:
- unemployment rate
- medication use
- blood pressure
- BMI

These predictors enter the level-1 model because they vary within individuals over time.

A simple form is:

$$
Y_{ij}
=
\pi_{0i}
+
\pi_{1i}TIME_{ij}
+
\pi_{2}X_{ij}
+
\epsilon_{ij}
$$

where $X_{ij}$ is a time-varying predictor.

$\pi_2$ describes the association between the outcome and the predictor at a particular occasion, conditional on the other terms in the model.

#### Centering time-varying predictors

Time-varying predictors can be represented in several ways, depending on the research question.

Possible representations include:
- raw values
- deviation from the grand mean
- deviation from a meaningful constant
- deviation from each person's own mean
- deviation from each person's initial value

These representations can change the interpretation of model parameters even when the underlying information is similar.

For example, within-person centering uses:

$$
X_{ij}-\bar X_i
$$

This represents how much the predictor at occasion $j$ differs from that individual's own average.

This can help distinguish:
- between-person differences: people who generally have higher $X$
- within-person changes: occasions when a person has higher or lower $X$ than usual

>[!tip]
>The choice of centering should be driven by substantive interpretation rather than a universal rule.

>[!warning] Endogeneity
>Associations involving time-varying predictors can be difficult to interpret causally.
>
>If $X_{ij}$ and $Y_{ij}$ change together, it may be unclear whether $X \rightarrow Y$ or $Y \rightarrow X$.
>
>This is especially important when the individual's current outcome can influence the value of the predictor itself. See [[LearningNotes/Causal inference\|Causal inference]].

# Functional form of time

Time can be modeled in different ways:
- linear time
- polynomial time
- piecewise time
- spline-based time
- categorical time
- other nonlinear forms

Choose the simplest form that adequately represents the data and research question.

>[!tip]
>The meaning of the intercept depends heavily on how TIME is coded. If $TIME=0$ means baseline, the intercept usually represents expected baseline status.

# Estimation & Model Comparison
## Estimation

Mixed models can be estimated using methods such as:
- [[LearningNotes/Maximum likelihood estimation\|maximum likelihood estimation (MLE)]]
	- full maximum likelihood (ML)
	- restricted maximum likelihood (REML)
- generalized least squares (GLS)
- iterative generalized least squares

>[!Tip]
>GLS = extending ordinary least squares by allowing residuals to be correlated and heteroscedastic, which is important for [[LearningNotes/Longitudinal Data Analysis\|longitudinal data]].

## Comparing models

For models estimated by ML, model fit can be compared using deviance:

$$
D=-2\log L
$$

Smaller deviance indicates better fit.

For two nested models:

$$
\Delta D=D_{reduced}-D_{full}
$$

This can be tested approximately using a $\chi^2$ distribution, with degrees of freedom equal to the difference in the number of estimated parameters.

This is the logic of the [[LearningNotes/Likelihood ratio test\|Likelihood ratio test]].

>[!important]
>Use ML, not REML, when comparing models that differ in fixed effects. REML is often preferred for estimating variance components in a final model.



## Variance reduction and pseudo-$R^2$

Variance components from simpler models can serve as baselines for evaluating later models.

For example:

$$
R^2_{pseudo}
=
\frac{\sigma^2_{baseline}-\sigma^2_{new}}
{\sigma^2_{baseline}}
$$

This describes the proportional reduction in unexplained variance after adding predictors.

Different variance components can have different pseudo-$R^2$ values:
- level-1 residual variance
- random-intercept variance
- random-slope variance

Interpretation:
- reduced random-intercept variance → predictor explains some baseline heterogeneity
- reduced random-slope variance → predictor explains some heterogeneity in rates of change
- reduced level-1 residual variance → predictor explains some within-person variation

>[!warning]
>Pseudo-$R^2$ should be interpreted cautiously because variance components can occasionally increase after adding predictors.

# Model assumptions and diagnostics

Important assumptions should be examined at both levels.

## Functional form

- Level 1: check whether the assumed TIME trajectory fits individual growth patterns
- Level 2: check whether relationships between growth parameters and predictors have the assumed form

## Residuals

Inspect residuals for:
- approximate normality
- homoscedasticity
- systematic patterns indicating model misspecification
- influential individual cases

Diagnostics are especially important for the final model being interpreted.

# Interpretation

## Fixed effects

Fixed effects describe the systematic population-level trajectory and predictor effects.

Examples:
- fixed intercept → expected outcome at the reference time point
- fixed effect of TIME → average rate of change
- predictor main effect → difference at the reference time point
- TIME × predictor interaction → difference in rate of change

## Random effects

Random effects describe how individual trajectories deviate from the population-average trajectory.

Important variance components:
- random-intercept variance → heterogeneity in initial status
- random-slope variance → heterogeneity in rates of change
- intercept-slope covariance → association between baseline deviations and rate-of-change deviations
- residual variance → remaining within-person variation

>[!hint]
>Variance components represent remaining unexplained heterogeneity conditional on the current fixed effects.

# Empirical Bayes estimates

Mixed models can estimate individual trajectories using model-based / empirical Bayes estimates.

These combine:

$$
\text{population information}
+
\text{individual information}
$$

rather than estimating each person's trajectory independently with OLS.

The resulting individual estimates are usually shrunk toward the relevant population-average trajectory, especially when an individual's data are sparse or noisy.

This often improves precision, but the quality of empirical Bayes estimates depends on the correctness of the fitted model.

# Practical workflow

>[!Core idea]
>First quantify variation, then model change over time, then explain individual differences in that change.

1. Explore the longitudinal structure.
2. Fit an unconditional means model.
3. Add TIME to fit an unconditional growth model.
4. Choose the functional form of TIME.
5. Add substantive predictors.
6. Decide how predictors should be centered or represented.
7. Add interactions with TIME if the question concerns change.
8. Examine variance reduction.
9. Compare nested models when appropriate.
10. Check assumptions and model fit.
11. Interpret fixed effects, random effects, and variance components.



