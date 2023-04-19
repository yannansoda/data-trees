---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Cross-Validation/","dgPassFrontmatter":true,"noteIcon":""}
---

## Why 
When you have training set and test set for model selection, one idea would be use the training set to estimate parameters for each model candidate, and then choose the model generates the least error to test data.

However, an extra parameter was chosen using the test set -> the generalisation error is underestimated. 

## How 
- split the data set into:
	- training set 
	- cross validation set (= validation/development/cv set) 
	- test set
- the ratios
	- traditionally, the ratios are train-dev-test = 70%-20%-20%
	- for large data set or in deep learning, the ratios can be train-dev-test = 98%-1%-1%
	- the dev and test sets should have similar distributions
- correspondingly, you will have training error, cross validation error, and test error (i.e. [[Notes/Cost Functions\|Cost Functions]] without regularization terms)


## Example: cross-validation for model selection
1. determine model options: number in polynomial/number of layers in neural network...
2. compute the model that generated least cross validation errors
3. then estimate the generalization error of the test set