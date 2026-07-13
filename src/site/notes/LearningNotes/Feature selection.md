---
{"topic":"DataScience, MachineLearning","dg-publish":true,"permalink":"/LearningNotes/Feature selection/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"DataScience, MachineLearning"}}
---

# What is Feature Selection
= Select a subset of all features for model training, usually in data preprocessing.
- Advantages
	- avoid the curse of dimensionality 
	- improves the predictive performance and interpretability of models
		- shorten training time
		- prevent overfitting
		- reduce generalization error
- Domain knowledge is important!!!

# Feature Selection methods
There are some of the techniques used for feature selection in data analysis.

| Method Type | Idea | Pros | Cons |
| ----------- | ---- | ---- | ---- |
| **Filter methods** | select features using statistics before modeling | simple and fast; good preprocessing step | can select redundant features; may ignore feature interactions |
| **Wrapper methods** | search feature subsets using model performance | can find feature combinations that work well together | slow; can overfit |
| **Embedded / Intrinsic methods** | feature selection happens during model training | efficient; directly connected to the model objective | model-dependent; selected features depend on chosen model |

## Filter methods
= select features before model training using statistical scores or simple rules
examples:
- **Variance Threshold**: remove features with very low variance
- **Correlation Filter**: remove one of two highly correlated features to reduce redundancy
- **Univariate statistical tests**: select features with higher correlation / association with target variables
	- ANOVA F-test
	- Chi-square test
	- mutual information
- **Feature importance-based filtering**: select features with higher [[LearningNotes/Interpretable Machine Learning#Feature Importance\|Interpretable Machine Learning#Feature Importance]] scores
	- via coefficient (linear regression, logistic regression) - but this may remove non-linear relationships
	- via impurity-based feature importances (tree-based models)

## Wrapper methods
= iterative process that repeatedly adds or removes subsets of features and checks model performance
examples:
- **Sequential Feature Selection (SFS)**
	- **Forward SFS**: start with 0 feature -> sequentially add feature
		1. select a significance level (SL, e.g. SL=0.05)
		2. fit all simple regression models. Select the one with the lowest P-value
		3. keep this variable and fit all possible models with one extra predictor added to the one(s) you already have.
		4. consider the predictor with the lowest P-value. If P < SL, go to step 3, otherwise go to FIN and keep the previous model
	- **Backward SFS**: start with all features -> sequentially remove feature
		1. select a significance level (SL, e.g. SL=0.05)
		2. fit the full model with all possible predictors
		3. consider the predictor with the highest P-value. If P > SL, remove the predictor; otherwise go to FIN
		4. fit model without this variable
		5. return to step 3
- **Bidirectional Elimination** (stepwise regression) = combination of Backward Elimination and Forward Selection
	1. select a significance level to enter and stay in the model (SL, e.g. SL=0.05)
	2. perform the next step of forward selection (new variables must have P < SL_enter to enter)
	3. perform all steps of backward elimination (old variables must have P < SL_stay to stay)
	4. repeat step 2 and 3, until no new variables can enter and no old variables can exit
- **Recursive Feature Elimination (RFE)**: repeatedly train a model and remove the least important features

## Embedded / Intrinsic methods
= model already performs feature selection during training, so no external selection tool is needed
examples:
- **Lasso / L1 regularization** [[LearningNotes/Cost Functions#^ed4ab0\|Cost Functions#^ed4ab0]]: can shrink some coefficients to exactly zero, so it performs feature selection
- **Ridge / L2 regularization** [[LearningNotes/Cost Functions#^aef45a\|Cost Functions#^aef45a]]: shrinks coefficients but usually does not set them to exactly zero, so it is not direct feature selection
- **Tree-based models**: a feature is not used in any split already means it may be less useful for the target variable
- **Tree-based Feature Importance**: use models like Random Forest / Gradient Boosting to rank features

# Feature Selection Stability
= checks whether selected features remain important across different samples of the data.
## Why it matters
- A feature selected once may be selected only because of one lucky train/test split.
- High-dimensional and correlated features can make feature lists unstable.
- Stable features are stronger candidates for interpretation or biomarker prioritization.
- For non-sparse models, a feature can appear important in one split but drop in rank in another split.
## Common approaches
- Resampling
	- see [[LearningNotes/Resampling-based Model Stability Checks#Common resampling schemes\|Resampling-based Model Stability Checks#Common resampling schemes]]
- Stability measures:

| Sparse/Non-sparse Model ([[LearningNotes/Sparse Model\|Sparse Model]]) | Model type              | What to track                         | Example stability measure              |
| ------------------------------------------ | ----------------------- | ------------------------------------- | -------------------------------------- |
| Sparse                                     | Sparse model            | selected / not selected features      | selection frequency                    |
| Non-sparse                                 | Linear non-sparse model | coefficient size and sign             | coefficient variance, sign consistency |
| Non-sparse                                 | Tree-based model        | feature importance scores             | rank correlation, top-k overlap        |
| Non-sparse                                 | Black-box model         | permutation importance or SHAP values | rank correlation, importance variance  |

## Typical workflow for sparse models
1. Subsample the training data many times
2. Fit a sparse model each time
3. Record which features are selected each time
4. Calculate selection frequency for each feature
5. Rank features by how often they are selected
## Typical workflow for non-sparse models
1. Resample the training data many times
2. Fit the model each time
3. Calculate feature importance each time, e.g. coefficients, permutation importance, tree-based importance, or SHAP values
4. Compare feature rankings or top-k important features across resamples
5. Check whether the same features remain consistently important


> [!Important]
> A model can have stable performance but unstable selected features, especially when features are highly correlated.
