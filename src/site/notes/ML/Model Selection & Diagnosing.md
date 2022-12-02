---
{"dg-publish":true,"permalink":"/ml/model-selection-and-diagnosing/"}
---

[[ML/Machine Learning\|Machine Learning]]
# cross-validation
## Why 
When you have training set and test set for model selection, one idea would be use the training set to estimate parameters for each model candidate, and then choose the model generates the least error to test data.
However, an extra parameter was chosen using the test set -> the generalisation error is underestimated. 
## How 
- split the data set into:
training set + 
cross validation set (= validation/development/cv set) + 
test set
- correspondingly, you will have training error, cross validation error, and test error (i.e. [[Mathcards/Cost Functions\|Cost Functions]] without regulaization terms)
- process example
	1. determine model options: number in polynomial/number of layers in neural network...
	2. compute the model that generated least cross validation errors
	3. then estimate the generalization error of the test set

# Error analysis
Take a subsample of the data and analyse error
  

Manually examine a sample of the training examples that the model misclassified in order to identify common traits and trends.

model-centric approach -> data-centric approach
data augmentation
modify an existing training example to create a new training example

data synthesis
use artificial data inputs to create a new training example

# Transfer learning
1. supervised pre-training 
download neural network with parameters that have been pre-trained on a large dataset with the same input type as your application.
2. fine tuning
further train the network on your data