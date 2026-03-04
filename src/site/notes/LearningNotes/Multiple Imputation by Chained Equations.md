---
{"topic":"Statistics, DataScience","dg-publish":true,"permalink":"/LearningNotes/Multiple Imputation by Chained Equations/","dgPassFrontmatter":true,"noteIcon":""}
---


>[!Tip] MICE vs. Fully Conditional Specification vs. Iterative Imputation
> MICE belongs to the Fully Conditional Specification (FCS) framework ([[LearningNotes/Handling Missing Data#Fully Conditional Specification (FCS)\|Handling Missing Data#Fully Conditional Specification (FCS)]])
> 
> MICE is generally the statistical method, while Scikit-learn’s IterativeImputer is a Python implementation.
## How MICE works
1. start with initial values: filling the missing values with initial values (e.g. mean)
2. iterate over each feature:
	1. Predict X1 using X2, X3 -> Replace missing X1
	2. Predict X2 using X1, X3 -> Replace missing X2
	3. Predict X3 using X1, X2 -> Replace missing X3
3. Repeat this cycle multiple times until convergence
4. Add randomness in predictions
5. Repeat whole process  for a number of iterations
### Why “Multiple” Imputation
- opposite to *single imputation* which fills in each missing value once
- instead make missing value a *distribution* of plausible values
#### Key steps
1. create N different complete datasets
2. each dataset has slightly different plausible imputed values
3. train/analyze each dataset separately
4. combine results (average coefficients, adjust variance)
### Why “Chained Equations”?
- In each iterative step, each feature with missing values is treated as a target to be predicted with other features

## Why use MICE
### Pros
- preserves statistical uncertainty
- preserves relationships between features
- allows flexible modeling:
	- Linear regression for continuous
	- Logistic regression for binary
	- Multinomial for categorical
	- Poisson for counts
	- Tree-based models (in some implementations)
- reduces bias, especially when
	- missingness rate is moderate (10–40%)
	- strong feature correlations exist
	- dataset is not extremely large
### Cons
- assumes Missing At Random [[LearningNotes/Handling Missing Data#^656f1e\|Handling Missing Data#^656f1e]]
- computationally heavier
- sensitive to model misspecification


