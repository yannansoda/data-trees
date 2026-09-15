---
{"topic":"DataScience","dg-publish":true,"permalink":"/LearningNotes/Regularization/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"DataScience"}}
---


# Regularization

## What is regularization
- Regularization = the process of adding information in order to solve an ill-posed problem or to prevent overfitting.
- Intuition:
Increasing the regularization parameter $\lambda$ ($\lambda$ >0) reduces overfitting by reducing the size of the parameters.  For some parameters that are near zero, this reduces the effect of the associated features.
> **Alternative intuition for deep neural networks:**
> Regularization reduces overfitting by letting the weight of units decay and get closer to 0 (given that $\lambda$ are usually large). If the weights almost zero, than the networks becomes almost linear and will avoid overfitting.


## Cost function with regularization
When you choose regularization, a regularization term will be added to the cost function.  
See [[LearningNotes/Cost Functions#Cost function with regularization\|Cost Functions#Cost function with regularization]].

## Types of Techniques
### Shrinking
- add penalty=reduce weight=weight decay
- the cost function thus aims to minimize the original loss + penalty (see [[LearningNotes/Cost Functions#Cost function with regularization\|Cost Functions#Cost function with regularization]])
#### L1/Lasso regularization
- penalization term = sum of the absolute values of the weights
- drives some weights to 0
	- good for models with fewer features, each of them has a large or median effect
	- produces a [[LearningNotes/Sparse Model\|Sparse Model]] and automatically performs [[LearningNotes/Feature selection\|Feature selection]]
>[!Tip] Sparse regularized models are often used for [[LearningNotes/Resampling-based Model Stability Checks#Feature selection stability\|feature selection stability]] and [[LearningNotes/Resampling-based Model Stability Checks#Stability Selection\|Stability Selection]]
#### L2/Ridge regularization
- penalization term = sum of the squares of the weights
- makes the biggest weights smaller
	- heavily punishing “outliers”, which are the very large parameters
	- good for models with many features, each of them has a small effect
>[!Quote] The Hundred-Page Machine Learning Book
>- If your only goal is to maximize the performance of the model on the holdout data, then L2 usually gives better results. L2 also has the advantage of being differentiable, so gradient descent can be used for optimizing the objective function.
#### Elastic Net
- combines L1 and L2: [[LearningNotes/Cost Functions#^d1942d\|Cost Functions#^d1942d]]
### Dropout regularization
{ #b76d6c}

- randomly knocking out units in neural network
- used only during training
- mostly used in computer vision (e.g. [[LearningNotes/Pattern Recognition\|Pattern Recognition]])
### Batch-normalization
- applies normalization on the inputs of hidden layers
- weakens the coupling between what the early layers parameters have to do and what the later layers parameters have to do. So it allows each layer of the network to learn by itself, a little bit more independently of other layers, and this has the effect of speeding up of learning in the whole network. 
- can add a slight regularization effect because of adding noise to hidden layers
### Data augmentation 
{ #933b29}

- usually in computer vision
- = generate more labeled images by taking labeled images and
	- flip them left/right
	- shift them up/down/right/left by a couple pixels
	- add small noise, etc...
-  but if the validation set doesn't have the same randomness, then the accuracy fluctuates crazily.
### Early stopping
- Initialize with small weights -> these get bigger as you do gradient descent- > stop when they are the ‘optimal’ size

 ![Pasted image 20230316144212.png\|300](/img/user/_assets/images/Pasted%20image%2020230316144212.png)
>[!interesting]
> But long-term training may lead to flip in large models, see [here](https://openai.com/research/deep-double-descent)
{ #9ff80e}


## Regularization in Bayesian framework
- A regularizing prior is a "skeptical" prior, which means it slows down the rate of the model in learning from the data.
- Multilevel models can be regarded as adaptive regularization, where the model itself tries to learn how skeptical it should be.
- It is a Bayesian method. It is the same device that non-Bayesian methods refer to as “penalized likelihood.”