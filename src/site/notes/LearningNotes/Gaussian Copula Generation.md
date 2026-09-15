---
{"topic":"Math, Modeling, Statistics","dg-publish":true,"permalink":"/LearningNotes/Gaussian Copula Generation/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"Math, Modeling, Statistics"}}
---

>[!abstract] Summary
>**Gaussian copula generation** is a way to generate multivariate synthetic data when each variable can have its own marginal distribution, but the dependency between variables is controlled by a Gaussian correlation structure.
>
>The key idea:
>1. sample correlated Gaussian variables
>2. convert them to uniform variables by the Gaussian CDF
>3. convert each uniform variable to the target distribution by that variable's inverse CDF
>
>So the Gaussian copula separates:
>- **marginal distribution**: what each variable looks like alone
>- **dependency structure**: how variables move together

# What is a copula
A **copula** is a function/model that links individual marginal distributions into a joint multivariate distribution. In simple terms, it describes the dependency between variables separately from what each variable's own distribution looks like.

# What problem does it solve
Often we want to simulate variables that are dependent, but not all normally distributed.

Example:
- age may be approximately continuous and skewed
- biomarker values may be log-normal
- disease status may be binary
- healthcare cost may be highly right-skewed

A plain multivariate normal model is too restrictive because it assumes all variables are Gaussian. A Gaussian copula lets us keep flexible marginals while still specifying a correlation matrix.

# Intuition
Think of Gaussian copula as generating the **rank-level dependency** first.

- Start with hidden correlated Gaussian variables
- Turn them into percentiles between 0 and 1
- Map those percentiles into whatever marginal distributions we want

So if two hidden Gaussian variables are positively correlated, high percentiles in one variable tend to appear with high percentiles in the other variable.

# Generation steps
Suppose we want to generate $d$ variables.

## 1. Specify a correlation matrix
Choose a valid correlation matrix $R$:

$$
R =
\begin{pmatrix}
1 & \rho_{12} & \cdots & \rho_{1d}\\
\rho_{21} & 1 & \cdots & \rho_{2d}\\
\vdots & \vdots & \ddots & \vdots\\
\rho_{d1} & \rho_{d2} & \cdots & 1
\end{pmatrix}
$$

This controls the dependency structure. See [[LearningNotes/Covariance & Correlation\|Covariance & Correlation]] and [[LearningNotes/Covariance Structure\|Covariance Structure]].

## 2. Sample from a multivariate normal distribution
Generate latent Gaussian variables:

$$
Z = (Z_1, ..., Z_d) \sim N(0, R)
$$

Here, each $Z_j$ is standard normal, but the variables are correlated according to $R$.

## 3. Convert Gaussian values to uniform values
Apply the standard normal CDF $\Phi$ to each dimension:

$$
U_j = \Phi(Z_j)
$$

Then:

$$
U_j \sim Uniform(0,1)
$$

The values are now percentiles, but still dependent.

## 4. Convert uniforms to target marginals
For each target variable with CDF $F_j$, use the inverse CDF:

$$
X_j = F_j^{-1}(U_j)
$$

Then $X_j$ follows the desired marginal distribution.

Example:
- $X_1 = F_{normal}^{-1}(U_1)$
- $X_2 = F_{lognormal}^{-1}(U_2)$
- $X_3 = F_{bernoulli}^{-1}(U_3)$

# Compact formula
The full transformation is:

$$
X_j = F_j^{-1}\left(\Phi(Z_j)\right), \quad Z \sim N(0,R)
$$

where:
- $R$: Gaussian correlation matrix
- $\Phi$: standard normal CDF
- $F_j^{-1}$: inverse CDF of the target marginal distribution

# Why it is useful
- Generate synthetic data with realistic dependency
- Simulate non-normal variables jointly
- Separate marginal modeling from dependency modeling
- Useful in risk modeling, health data simulation, finance, and sensitivity analysis

# Limitations
- The dependency is still Gaussian-like, so it may miss tail dependence
- The input correlation matrix must be valid / positive semi-definite
- Correlation after transformation may not exactly equal the original $R$
- Discrete variables can create ties and make correlation harder to control

>[!important]
>Gaussian copula is not saying the observed variables are Gaussian. It only uses a hidden Gaussian layer to create dependency.

>[!info] Related Notes
>- [[LearningNotes/Covariance & Correlation\|Covariance & Correlation]]
>- [[LearningNotes/Covariance Structure\|Covariance Structure]]
>- [[LearningNotes/Cumulative Distribution Function (CDF)\|Cumulative Distribution Function (CDF)]]
>- [[LearningNotes/Monte Carlo Method\|Monte Carlo Method]]
>- [[LearningNotes/Random Variables & Probability distributions\|Random Variables & Probability distributions]]
