---
{"topic":"DataScience","dg-publish":true,"permalink":"/Notes/Regularization/","dgPassFrontmatter":true,"noteIcon":""}
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
See [[Notes/Cost Functions#Cost function with regularization\|Cost Functions#Cost function with regularization]].

## Types of Techniques
- shrinking (= add penalty/reduce weight/weight decay)
	- L1 regularization (lasso): [[Notes/Cost Functions#^19a2bf\|Cost Functions#^19a2bf]]
{ #6700d3}

	- L2 regularization (ridge, "weight decay"): [[Notes/Cost Functions#^b2a01f\|Cost Functions#^b2a01f]]
{ #1e9ee5}

	- elastic net regularization 
{ #de0043}

		- = L1 + L2 regularization: $$ ElasticNet \ Penalty = λ_1 \sum_{j=1}^p​∣ \beta_j​∣+ \lambda_2​ \sum _{j=1}^p​ \beta_j^2$$, where $\lambda_1$ and $\lambda_2$​ are tuning parameters that control the strength of the L1 and L2 penalties, respectively.
	- dropout regularization
{ #b76d6c}

		- randomly knocking out units in neural network
		- mostly used in computer vision (e.g. [[Notes/Pattern Recognition\|Pattern Recognition]])
- batch-normalization
- data augmentation 
{ #933b29}

	- usually in computer vision
	- = generate more labeled images by taking labeled images and
		- flip them left/right
		- shift them up/down/right/left by a couple pixels
		- add small noise, etc...
	-  but if the validation set doesn't have the same randomness, then the accuracy fluctuates crazily.
- early stopping
	- Initialize with small weights -> these get bigger as you do gradient descent- > stop when they are the ‘optimal’ size
	- ![Pasted image 20230316144212.png|300](/img/user/assets/images/Pasted%20image%2020230316144212.png)
>[!interesting]
> But long-term training may lead to flip in large models, see [here](https://openai.com/research/deep-double-descent)
{ #9ff80e}


## Regularization in Bayesian framework
- A regularizing prior is a "skeptical" prior, which means it slows down the rate of the model in learning from the data.
- Multilevel models can be regarded as adaptive regularization, where the model itself tries to learn how skeptical it should be.
- It is a Bayesian method. It is the same device that non-Bayesian methods refer to as “penalized likelihood.”