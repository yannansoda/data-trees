---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Recurrent Neural Networks (RNN)/","dgPassFrontmatter":true,"noteIcon":""}
---


>[!reference]
>https://towardsdatascience.com/recurrent-neural-networks-rnns-3f06d7653a85
# Why recurrent
RNNs are called ==recurrent== because they perform the same task for every element of a sequence, with the output being depended on the previous computations. 
Another way to think about RNNs is that they have a “memory” which captures information about what has been calculated so far.

# Architecture and components 
![assets/images/RNN-1.png|400](/img/user/assets/images/RNN-1.png)
$$h(t)=f(Ux(t)+Wh(t−1))$$
- $h(t)$ is the hidden state at time t
- $x(t)$ is the input at time t
- $U$, $W$, and $V$ are weights for input-to-hidden connections, hidden-to-hidden recurrent connections, and hidden-to-output connections, respectively.
- The function f is taken to be a non-linear transformation such as tanh, ReLU.
- $o(t)$ illustrates the output of the network and is also often subjected to non-linearity

### Forward pass
![](/img/user/assets/images/RNN-2.png)

### Backward pass
The gradient computation involves performing a forward propagation pass moving left to right through the graph shown above followed by a backward propagation pass moving right to left through the graph. 

# RNNs & Memory

![RNN-10.png|400](/img/user/assets/images/RNN-10.png)

# Pros & Cons
- Pros: handle long-range dependency
- Cons: inefficient, gradient vanishing/exploding
	- [[Notes/Transformer\|Transformer]] may work as a better alternative