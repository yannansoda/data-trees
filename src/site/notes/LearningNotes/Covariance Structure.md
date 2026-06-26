---
{"topic":"Statistics","dg-publish":true,"permalink":"/LearningNotes/Covariance Structure/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"Statistics"}}
---

# Overview

## What is covariance structure
- **Covariance structure** describes the assumed pattern of variance and covariance among multiple observations or variables.
- In simple terms, it answers:
	- how variable is each measurement?
	- how related are different measurements to each other?
	- does the relationship follow a pattern?
- It is closely related to [[LearningNotes/Covariance & Correlation\|Covariance & Correlation]], but more applied: instead of only calculating covariance, we specify how covariance should behave in a model
## Intuition
Think of covariance structure as the model's assumption about similarity.
It tells the model:
> Which observations should be treated as more similar, and by how much?
## Why covariance structure matters
- Many statistical models need assumptions about dependency:
	- vanilla case
		- observations are independent
		- -> each observation has its own variance
		- -> covariance between different observations is 0
	- many real cases
		- observations are not independent (repeated measurements ([[LearningNotes/Longitudinal Data Analysis\|Longitudinal Data Analysis]]), [[LearningNotes/Time Series\|time series]], hierarchical or clustered data)
		- -> covariance is not 0 and has some structures
		- -> the model needs to know what relationship pattern to assume

>[!important] If the covariance structure is wrong, estimates may look reasonable, but the uncertainty can be wrong. This can lead to misleading inference.

## Where covariance structures are used
### Repeated-measures and longitudinal models
- Used to model how measurements from the same subject are correlated over time. See [[LearningNotes/Longitudinal Data Analysis\|Longitudinal Data Analysis]].
- Example: a patient's blood pressure this week is usually more similar to last week than to one year ago.
### Time series models
- Used to model dependency across [[LearningNotes/Time Series\|time series]].
- Example: today's stock price is usually more related to yesterday's price than to last year's price.
### Spatial models
- Used to model dependency across locations.
- Example: temperatures from nearby cities are usually more similar than temperatures from distant cities.
### Multivariate models
- Used when modeling several outcomes together.
- Example: height, weight, and blood pressure may have covariance with each other.
### Mixed-effects models
- Used in [[LearningNotes/Linear Mixed Models\|Linear Mixed Models]] and other mixed-effects models to describe dependency within subjects, groups, or clusters.
- In this context, covariance structure helps model repeated or clustered observations that are not independent.
# Common covariance structures
## Independent (simplest structure)
Assumption:
- observations are not correlated with each other
- covariances between different observations are 0
Use when:
- observations are genuinely independent, as often assumed in basic [[LearningNotes/Regression\|Regression]]
- there is no repeated, temporal, spatial, or grouped dependency

## Compound symmetry (CS)
Assumption:
- all measurements have the same variance
- every pair of measurements has the same covariance / correlation

Example:
```text
corr(time1, time2) = corr(time1, time4)
```

Use when repeated measurements are equally related, no matter how far apart they are.

Example situation:
- conditions are measured in random order
- there is no meaningful time or distance relationship
## Autoregressive order 1, AR(1)
Assumption:
- closer measurements are more correlated
- farther measurements are less correlated

Example:
```text
corr(time1, time2) > corr(time1, time4)
```

This makes sense for ordered data.

Example situations:
- longitudinal data
- time series data
- repeated measurements where time distance matters, such as in [[LearningNotes/Longitudinal Data Analysis\|Longitudinal Data Analysis]]

## Unstructured (UN)
Assumption:
- no simple pattern is imposed
- every variance and covariance is estimated separately

This is very flexible, but needs more data.

Use when:
- you do not want to assume a specific correlation pattern
- you have enough observations to estimate the covariance parameters, often through [[LearningNotes/Maximum likelihood estimation\|Maximum likelihood estimation]] or related methods

Problem:
- it can overfit
- it may fail or become unstable if the dataset is small

## Heterogeneous structures
The **H** usually means variances are allowed to differ across measurements or time points.

Example:
```text
variance(time1) ≠ variance(time2) ≠ variance(time3)
```

This is useful when measurements become more or less variable over time or across conditions.

Common examples:
- **CSH**: compound symmetry with heterogeneous variances
- **ARH(1)**: AR(1)-type correlation with heterogeneous variances


