---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Gradient Descent/","dgPassFrontmatter":true,"noteIcon":""}
---

# What does Gradient Descent do
It minimizes cost function using derivatives by proceeding in epochs (an epoch consists of using the training set entirely to update each parameter).

# Gradient descent in Neural networks
- use forward-propagation to calculate the values of each layer
- use back-propagation to calculate the derivatives 
- example of a two-layer logistic regression neural network by Andrew Ng:
![Pasted image 20230310114003.png|500](/img/user/assets/images/Pasted%20image%2020230310114003.png)

# Types of Gradient Descent

>[!Quote]
>From The Hundred-Page Machine Learning Book:
>
>- Minibatch stochastic gradient descent (minibatch SGD) is a version of the algorithm that speeds up the computation by approximating the gradient using smaller batches (subsets) of the training data. 
>- SGD itself has various “upgrades”. 
>	- Adagrad is a version of SGD that scales $\alpha$ for each parameter according to the history of gradients. As a result, $\alpha$ is reduced for very large gradients and vice-versa. 
>	- Momentum is a method that helps accelerate SGD by orienting the gradient descent in the relevant direction and reducing oscillations. 
>	- In neural network training, variants of SGD such as RMSprop and Adam, are very frequently used.

### Outline of Types
- Batch gradient descent 
- Stochastic gradient descent (SGD)
	- considers **each training observation individually**, instead of all at once (as batch/basic gradient descent would)
	- Instead of calculating the exact gradient of the cost function, it uses each observation to estimate the gradient and then takes a step in that direction. While each individual observation will provide a poor estimate of the true gradient, given enough randomness the parameters will converge to a good global estimate. 
	- but still, may lead to erratic updates
- [[Notes/Gradient Descent#Mini-batch gradient Descent\|#Mini-batch gradient Descent]]
- [[Notes/Gradient Descent#Momentum\|#Momentum]]
- [[Notes/Gradient Descent#RMSprop (Root Mean Square prop)\|#RMSprop (Root Mean Square prop)]]
-  [[Notes/Gradient Descent#Adam (Adaptive Moment Estimation)\|#Adam (Adaptive Moment Estimation)]]
- [[Notes/Gradient Descent#Learning rate decay\|#Learning rate decay]]
### Batch gradient descent vs. Stochastic gradient descent
- Batch gradient descent: most basic approach
- Stochastic gradient descent: a variant of batch gradient descent where the weights are updated after computing the gradient of the loss function with respect to a single training example at a time
- Comparison
	- batch ones are slow; stochastic ones can avoid local minimum but can be noisy
	- different ways to update weights
![/assets/images/artificial-nn2.png|500](/img/user/assets/images/artificial-nn2.png)

### Mini-batch gradient Descent
- Mini-batch a compromise between batch and stochastic gradient descent, where the weights are updated after computing the gradient of the loss function with respect to a small batch of training examples (typically between 32 and 512).
- Comparison
 ![Pasted image 20230424102038.png|500](/img/user/assets/images/Pasted%20image%2020230424102038.png)
![Pasted image 20230316184519.png|500](/img/user/assets/images/Pasted%20image%2020230316184519.png)
- when to use 
	- when the data size is very large (>= 2000)
- what to use
	- if  $n_{batch}$ = m: batch gradient descent 
	- if  $n_{batch}$ = 1: stochastic gradient descent 
	- usually $n_{batch} = 2^n$: 64, 128, ...
- it should fit in CPU/GPU memory

### Exponentially weighted averages
(Exponentially weighted moving averages)
- describes the trend using local averages
### Momentum 
- The idea behind gradient descent with momentum is to add a "momentum" term to the weight update rule (stochastic gradient descent) that encourages the weight updates to continue in the same direction as the previous updates. 
- This can help to accelerate convergence and reduce oscillations in the optimization process.
- The weight update rule for gradient descent with momentum can be written as:
$$ v(t) = \gamma * v(t-1) + learning \ rate * gradient$$
$$weight(t) = weight(t-1) - v(t)$$
where v(t) is the "velocity" vector at time t, $\gamma$ is the momentum coefficient (typically set to a value between 0.9 and 0.99), learning rate is the step size or learning rate, gradient is the gradient of the loss function with respect to the weights, and weight(t) is the weight vector at time t.
### RMSprop (Root Mean Square prop)

### Adam (Adaptive Moment Estimation)  
- Adam is a combination of two other optimization algorithms, namely, stochastic gradient descent with momentum and RMSprop.

### Learning rate decay 
- reduce the learning rate over time as the optimization process progresses. 
- the idea behind learning rate decay is that as the algorithm gets closer to the minimum of the loss function, it may benefit from smaller steps to avoid overshooting or oscillations around the minimum.
- can be combined with other algorithms such as SGD and Adam
