---
{"topic":"Statistics","dg-publish":true,"permalink":"/StudyNotes/Linear mixed models/","dgPassFrontmatter":true,"noteIcon":""}
---

# What is LMM
- Also known as a linear mixed effects model, it is a statistical model that combines **both fixed and random** effects to analyze data that exhibit both within-group and between-group variability.
- "linear": the model is a linear regression model, where the response variable is assumed to be a linear combination of the predictor variables. 
- "mixed": the model includes both 
	- fixed effects (population characteristics)
		- the same as in a standard linear regression model= the average effect of the predictor variables on the response variable across all levels of the random effects
	- random effects (individual characteristics)
		- account for the variability between subjects or groups; allow for the effects of the predictor variables to vary across different groups or clusters of data
- Formula: 
 $$Y = X\beta + Zb + \epsilon$$
	- where $Y$ is a vector of responses, $X$ and $Z$ are design matrices, $\beta$ and $b$ are vectors of fixed and random effects, respectively, and $\epsilon$ is a vector of residual errors.
	- These coefficients represent the average effect of the predictor variables on the response variable across all levels of the random effects.
	- Compared to [[StudyNotes/Anova & Post-hoc\|Anova & Post-hoc]], ANOVA does not have the random effect part:
	- $$Y = X\beta + \epsilon$$
# Why LLM matters
Compared to [[StudyNotes/Anova & Post-hoc\|Anova & Post-hoc]], it is more generalized: 
- It can handle non-independent data that exhibit within-group correlation, such as repeated measures or longitudinal data, or data that involve different levels of grouping, such as hierarchical or nested data.
- It can handle all types of data: continuous, discrete, categorical, ordinal
- It can handle unbalanced or missing data 

# Assumptions for using LLM
- subjects are random sample from the population of interest
- the values of the dependent variable have a multivariate normal distribution with covariance structure
>[!five well known covariance structure]
>- UN (Unstructured)
>- CS (Compound Symmetry):
>	- all variances are equal, and all pairwise covariances are equal
>- CSH (Compound Symmetry Heterogeneous)
>- AR(1) (Autoregressive of order 1)
>- ARH(1) (Autoregressive Heterogeneous of order 1)
- data from different individuals are independent, while repeated measurements of the same individual are not assumed to be independent
- missing data are assumed to be ignorable

# What to determine when using LLM
- the best covariance structure
- the best model among:
	- random intercepts + fixed slopes
	- fixed intercepts + random slopes
	- random intercepts + random slopes