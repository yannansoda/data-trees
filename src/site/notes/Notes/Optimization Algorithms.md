---
{"topic":"Math, MachineLearning, DeepLearning","dg-publish":true,"permalink":"/Notes/Optimization Algorithms/","dgPassFrontmatter":true,"noteIcon":""}
---

## Convex optimization
- [[_assets/images/Convexity\|Convexity]]

## Gradient descent
- [[Notes/Gradient Descent\|Gradient Descent]]

## Optimization challenges
### Common challenges
- local minima
- saddle points
	- any location where all gradients of a function vanish but which is neither a global nor a local minimum
	- ![Pasted image 20241008162502.png|200](/img/user/_assets/images/Pasted%20image%2020241008162502.png)
### Challenges in DL
- - Almost all optimization problems arising in deep learning are nonconvex
- Vanishing / Exploding gradients
{ #4a1546}

	- Vanishing gradients: the gradients of a neural network's loss function become extremely small, causing the weights to update very slowly and making it difficult for the network to learn effectively
	- Exploding gradients: gradients become excessively large, leading to unstable updates and causing the model's parameters to oscillate or diverge during training

## How to speed up optimization in DL
- Normalizing inputs
	- for tanh: Xavier initialization
	- for ReLU: He Initialization
- Gradient checking
	- only use in debugging
	- remember regularization
	- doesn't work for dropout
- Hyperparameter Tuning: [[Notes/Hyperparameter Tuning#Hyperparameter Tuning in Deep Learning\|Hyperparameter Tuning#Hyperparameter Tuning in Deep Learning]]
- Batch Normalization


