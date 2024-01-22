---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Artificial Neural Networks/","dgPassFrontmatter":true,"noteIcon":""}
---


>[!Interesting] Neural network playground
>https://playground.tensorflow.org/
# Basic working mechanism
![artificial-nn-1.png|600](/img/user/assets/images/artificial-nn-1.png)
# How it works
1. Randomly initialise the weights to small numbers close to 0 (but not 0).
2. Input the first observation of your dataset in the input layer, each feature in one input node.
3. **Forward-propagation**: from left to light, the neurons are activated in a way that the impact of each neuron's activation is limited by the weights. Propagate the activations until getting the predicted result y.
4. Compare the predicted result to the actual result. Measure the generated error.
5. **Back-propagation**: from right to left, the error is propagated. Update the weights according to how much they are responsible for the error. The learning rate decides by now much we update the weights.
6. Repeat Steps 1 to 5 and update the weights after each observation (**Reinforcement Learning**); OR: Repeat Steps 1 to 5 but update the weights only after a batch of observations (**Batch Learning**).
7. When the whole training set passed through the ANN, that makes an epoch. Redo more epochs. 

# Epoch vs. Batch
- 1 batch = a group of samples
- 1 epoch = touching each sample once, which contains multiple batches

# Activation functions
### There are multiple forms
- sigmoid 
$$
\phi(z) = \frac{1}{1 + e ^ z}
$$
![Pasted image 20230309212108.png|300](/img/user/assets/images/Pasted%20image%2020230309212108.png)
- tanh = a shifted sigmoid with a mean as 0
$$
\phi(z) = \frac{e^z - e^{-z}}{e^z+e^{-z}}
$$
![Pasted image 20230309212317.png|300](/img/user/assets/images/Pasted%20image%2020230309212317.png)
- Softmax
$$\phi(z) = \text{Softmax}(z_{i}) = \frac{\exp(z_i)}{\sum_j \exp(z_j)}$$
> Why "soft": because it generates values between 0 and 1 and sum to 1, so the max value is a probability smaller than 1, instead of "hard" max value as 1 and the rest as 0.


- rectifier (ReLU) -  when you must model a piecewise linear target
$$
\phi(z) = max(z, 0)
$$
> An alternative (better) version of ReLU is **leaky ReLU**.


- Linear activation function
$$
\phi(z) = az + b
$$
- Hyperbolic Tangent (tanh)
$$
\phi(z) = \frac{1 - e^{-2z}}{1+e^{-2z}}
$$


### Which to choose depends on your problems:
- for the output layer:
	- binary classification -> sigmoid
	- multiclass classification -> Softmax
	- regression -> linear activation & ReLU
- for hidden layers: 
	- use default function (usually ReLU, because it is faster)
	> Andrew Ng: 
	> If you're not sure what to use for your hidden layer, I would just use the ReLu activation function that's what you see most people using these days.
	- tanh is better than sigmoid
	- do not use linear activation
- Different forms can be combined, e.g. using rectifier in the hidden layer and then sigmoid in output layer
>[!Tips] Why ReLU is faster than sigmoid-like activation functions?
> Because minimizing loss function requires [[Notes/Gradient Descent\|Notes/Gradient Descent]], whose speed depends on the derivative of the activation function $\phi (z)$. Both derivatives of sigmoid and tanh functions become very small when $\phi (z)$, in other words, gradient descent becomes very slow. But this won't happen to ReLU, because its derivative is a constant (when $z>0$).

