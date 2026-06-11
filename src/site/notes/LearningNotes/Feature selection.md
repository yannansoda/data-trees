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
There are some of the techniques used for feature selection in data analysis

| Method                | Pros                                                                                                                            | Cons                                                                   |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Intrinsic methods** | fast and no external selection tool is needed; provide a direction connection between feature selection and the object function | model-dependent; the choice of models is limited                       |
| **Filter methods**    | simple and fast; can capture the large trends in the data                                                                       | tend to select redundant features; ignore relationships among features |
| **Wrapper methods**   | search for a wider variety of features                                                                                          | tend to overfit; slow                                                  |

## Intrinsic methods
- embedded methods or implicit methods: model already can handle it, do not require extra methods
- examples
	- tree-based models: a feature is not used in any split already means it is independent of the target variable
	- regularizaton models (Lasso regression [[LearningNotes/Cost Functions#^ed4ab0\|Cost Functions#^ed4ab0]], Ridge Regression [[LearningNotes/Cost Functions#^aef45a\|Cost Functions#^aef45a]]): only keep features with non-zero coefficients 

## Filter methods
- select features that correlate well with target variables 
- examples
	- univariate statistical analysis: select features with higher correlations with target variables
	- feature importance-based: select features with higher [[LearningNotes/Interpretable Machine Learning#Feature Importance\|Interpretable Machine Learning#Feature Importance]] scores
		- via coefficient (linear regression, logistic regression) - but this may remove non-linear relationships
		- via impurity-based feature importances (tree-based models)

## Wrapper methods
- iterative process that repeatedly add subjects of feature to the model
- examples
	- **Sequential Feature Selection (SFS)**
		- **Forward SFS**: start with 0 feature -> sequentially add feature
			1. select a significance level (SL, e.g. SL=0.05)
			2. fit all simple regression models. Select the one with the lowest P-value
			3. keep this variable and fit all possible models with one extra predictor added to the one(s) you already have.
			4. consider the predictor with the lowest P-value. If P < SL, go to step 3, otherwise go to FIN and keep the previous model
		- **Backward SFS** ( (Recursive Feature Elimination, fastest):  start with all features->  sequentially remove feature
			1. select a significance level (SL, e.g. SL=0.05)	2. fit the full model with all possible predictors
			2. consider the predictor with the highest P-vales. If P > SL, go to step 4, otherwise go to FIN
			3. remove the predictor
			4. fit model without this variable
			5. return to step 3
	- **Bidirectional Elimination** (stepwise regression) = combination of Backward Elimination and Forward Selection
		1.  select a significance level to enter and stay in the model (SL, e.g. SL=0.05)
		2. perform the next step of forward selection (new variables must have P < SL_enter to enter)
		3. perform all steps of backward elimination (old variables must have P < SL_enter to stay)
		4. repeat step 2 and 3, until no new variables can enter and no old variables can exit

# Feature Selection Stability
= checks whether selected features remain important across different samples of the data.
- Usually measured with [[LearningNotes/Resampling-based Model Stability Checks\|Resampling-based Model Stability Checks]]
- In sparse models, selection frequency is often used as a stability measure
## Why it matters
- A feature selected once may be selected only because of one lucky train/test split.
- High-dimensional and correlated features can make feature lists unstable.
- Stable features are stronger candidates for interpretation or biomarker prioritization.
## Common approaches
see [[LearningNotes/Resampling-based Model Stability Checks#Common resampling schemes\|Resampling-based Model Stability Checks#Common resampling schemes]]
## Typical workflow
1. Subsample the training data many times
2. Fit a sparse model each time
3. Record which features are selected each time
4. Calculate selection frequency for each feature
5. Rank features by how often they are selected
## Stability Selection
- A formal feature selection framework.
- Repeatedly fits sparse models on subsampled data.
- Ranks features by selection frequency.
- Features selected frequently are considered more stable.

> [!Important]
> A model can have stable performance but unstable selected features, especially when features are highly correlated.