---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Problems in Classification/","dgPassFrontmatter":true,"noteIcon":""}
---

# How to handle Multiclass Classification

### Extend algorithms from binary classification to multiclass classification
- Logistic regression: replacing the sigmoid function with the softmax function 
- kNN 
### 'One versus rest' strategy
- The idea is to transform a multiclass problem into C binary classification problems and build C binary classifiers.

>[!Quote] The Hundred-Page Machine Learning Book
>For example, if we have three classes, y ∈{1,2,3}, we create copies of the original datasets and modify them. 
>- In the first copy, we replace all labels not equal to 1 by 0. In the second copy, we replace all labels not equal to 2 by 0. In the third copy, we replace all labels not equal to 3 by 0. Now we have three binary classification problems where we have to learn to distinguish between labels 1 and 0, 2 and 0, and 3 and 0.
>- Once we have the three models, to classify the new input feature vector 𝐱, we apply the three models to the input, and we get three predictions. 
>- We then pick the prediction of a non-zero class which is **the most certain**. Remember that in logistic regression, the model returns not a label but a score (between 0 and 1) that can be interpreted as the probability that the label is positive. We can also interpret this score as the certainty of prediction.

# How to handle One-Class Classification
One-Class Classification 
- = distinguish one class from everything else
- = unary classification/class modelingn
### One-class Gaussian
### One-class k-means
### One-class kNN
### one-class SVM

# How to handle Multilabel Classification