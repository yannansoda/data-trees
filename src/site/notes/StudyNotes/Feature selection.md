---
{"topic":"DataScience","dg-publish":true,"permalink":"/StudyNotes/Feature selection/","dgPassFrontmatter":true,"noteIcon":""}
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

### Intrinsic methods
- embedded methods or implicit methods: model already can handle it, do not require extra methods
- examples
	- tree-based models: a feature is not used in any split already means it is independent of the target variable
	- regularizaton models (Lasso regression [[StudyNotes/Cost Functions#^ed4ab0\|Cost Functions#^ed4ab0]], Ridge Regression [[StudyNotes/Cost Functions#^aef45a\|Cost Functions#^aef45a]]): only keep features with non-zero coefficients 

### Filter methods
- select features that correlate well with target variables 
- examples
	- univariate statistical analysis: select features with higher correlations with target variables
	- feature importance-based: select features with higher [[StudyNotes/Interpretable Machine Learning#Feature Importance\|Interpretable Machine Learning#Feature Importance]] scores
		- via coefficient (linear regression, logistic regression) - but this may remove non-linear relationships
		- via impurity-based feature importances (tree-based models)

### Wrapper methods
- iterative process that repeatedly add subjects of feature to the model
- examples
	- sequential feature selection (SFS)
		- Forward SFS: start with 0 feature -> sequentially add feature
			1. select a significance level (SL, e.g. SL=0.05)
			2. fit all simple regression models. Select the one with the lowest P-value
			3. keep this variable and fit all possible models with one extra predictor added to the one(s) you already have.
			4. consider the predictor with the lowest P-value. If P < SL, go to step 3, otherwise go to FIN and keep the previous model
		- Backward SFS ( (Recursive Feature Elimination, fastest):  start with all features->  sequentially remove feature
			1. select a significance level (SL, e.g. SL=0.05)	2. fit the full model with all possible predictors
			2. consider the predictor with the highest P-vales. If P > SL, go to step 4, otherwise go to FIN
			3. remove the predictor
			4. fit model without this variable
			5. return to step 3
	- Bidirectional Elimination (stepwise regression) = combination of Backward Elimination and Forward Selection
		1.  select a significance level to enter and stay in the model (SL, e.g. SL=0.05)
		2. perform the next step of forward selection (new variables must have P < SL_enter to enter)
		3. perform all steps of backward elimination (old variables must have P < SL_enter to stay)
		4. repeat step 2 and 3, until no new variables can enter and no old variables can exit