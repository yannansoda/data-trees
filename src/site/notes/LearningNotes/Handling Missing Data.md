---
{"topic":"DataScience, MachineLearning, Statistics","dg-publish":true,"permalink":"/LearningNotes/Handling Missing Data/","dgPassFrontmatter":true,"noteIcon":""}
---


# Type of data missing
### Understanding why data is missing
- **Missing Completely At Random (MCAR)**: missing entirely by chance, independent of any observed or unobserved values
- **Missing At Random (MAR)**: missing depends on _only_ on the observed values of _other_ features, not on the missing value itself
{ #656f1e}

	- example: older individuals have less data records
- **Missing Not At Random (MNAR):** probability being missing depends on the missing value *itself* or on other unobserved factors
	- example: patients with severe symptoms drop out of a clinical trial.

# Handling missing data

| Method Type                          | Method                                              | How it Works                                                                                                                            | Data Missing Type            | Strengths                                          | Key Risks / Notes                              |
| :----------------------------------- | :-------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- | -------------------------------------------------- | ---------------------------------------------- |
| Deletion                             | List-wise deletion                                  | Remove any row with ≥1 missing value                                                                                                    | MCAR                         | Simple                                             | Large data loss                                |
| Deletion                             | Pair-wise deletion                                  | Use all available data per calculation (e.g., correlations)                                                                             | MCAR                         | Retains more data than list-wise                   | Can produce inconsistent covariance matrices   |
| Single Imputation (Deterministic)    | Mean / Median / Mode Imputation                     | - use mean/median for continuous value<br>- use mode for discrete value                                                                 | MCAR                         | Simple                                             | Underestimates variance; distorts correlations |
| Single Imputation (Deterministic)    | Constant / Out of the range                         | Use specific values within/out of the range                                                                                             | None (mechanism-agnostic)    | Keeps missingness signal                           | Must add missing indicator; otherwise biased   |
| Single Imputation + Indicator        | Missing Indicator Method                            | - replaces each missing value by a zero / binary flag<br>- works for regression: extends the regression model by the response indicator | MAR                          | Captures missingness pattern                       | Can bias linear models; safer in trees         |
| Single Imputation (Model-based)      | Regression imputation                               | predict the value by building an interpolator or predicting them based on other features                                                | MAR                          | Preserves relationships                            | Underestimates variance                        |
| Single Imputation (Model-based)      | Stochastic regression imputation                    | enhanced regression imputation, where **Imputed Value = Regression Prediction + Random Error**                                          | MAR                          | Preserves variance better                          | Still single dataset (no pooling)              |
| Time-Series Imputation               | Last observation carried forward (LOCF)             | Use previous timepoint value<br>                                                                                                        | Implicitly assumes no change | Simple for longitudinal                            | underestimates variability                     |
| Time-Series Imputation               | Baseline observation carried forward (BOCF)         | Use baseline value for all missing                                                                                                      | Implicitly assumes no change | Simple for longitudinal                            | underestimates dynamic                         |
| Time-Series Imputation               | Interpolation (Linear / Spline)                     | Interpolate using adjacent timepoints                                                                                                   | MAR + smoothness assumption  | Good for dense time series                         | Fails for abrupt changes                       |
| Single Imputation (Similarity-based) | [[LearningNotes/K-Nearest Neighbor\|K-Nearest Neighbor]] imputation                   | Use similar samples to fill missing values                                                                                              | MAR                          | Non-parametric; captures local structure           | Poor in high dimensions; ignores uncertainty   |
| Multiple Imputation                  | [[Multiple Imputation by Chained Equations \|Multiple Imputation by Chained Equations ]](MICE) | Iteratively model each variable conditionally                                                                                           | MAR                          | Flexible; works with mixed data types              | Expensive                                      |
| Multiple Imputation                  | Joint Modeling Multiple Imputation                  | Model full multivariate distribution (often MVN)                                                                                        | MAR                          | Statistically coherent                             | Strong distributional assumptions              |
| Multiple Imputation                  | Multilevel / Hierarchical Multiple Imputation       | MI including random effects for clustered/longitudinal data                                                                             | MAR                          | Respects within-subject correlation                | More complex implementation                    |
| Multiple Imputation                  | Predictive Mean Matching (PMM)                      | Impute by matching predicted values to observed donors                                                                                  | MAR                          | Produces realistic values; robust to non-normality | Needs sufficient donor pool                    |
| Likelihood-Based (No Imputation)     | Mixed-Effects Model (FIML)                          | Fit longitudinal model directly using all available data (no explicit imputation)                                                       | MAR                          | Statistically efficient                            | Only works if analysis model supports it       |
| Longitudinal Grid Imputation         | Time-Raster Imputation                              | Insert regular time grid and impute at grid level                                                                                       | MAR                          | Handles irregular timepoints                       | Requires structured modeling                   |

# Stats Behind: Model-Based Imputation Frameworks
There are three major statistical frameworks for handling missing data in model-based settings.
### Joint Modeling (JM)
- model the full multivariate distribution directly
- impute from the joint distribution
- Examples:
	- Multivariate Normal Multiple Imputation
	- Bayesian joint models
### Fully Conditional Specification (FCS)
- model each variable conditionally on others
- erate through variables sequentially
- Examples:
	- [[LearningNotes/Multiple Imputation by Chained Equations\|Multiple Imputation by Chained Equations]]
	- MissForest (single imputation, non-parametric)
### Likelihood-Based Methods (No Imputation)
- do not fill missing values
- estimate model parameters directly using all observed data
- Examples:
	- Mixed-effects models with FIML
	- Structural equation modeling with FIML