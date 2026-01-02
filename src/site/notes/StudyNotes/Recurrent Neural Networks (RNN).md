---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Recurrent Neural Networks (RNN)/","dgPassFrontmatter":true,"noteIcon":""}
---


>[!reference]
>https://towardsdatascience.com/recurrent-neural-networks-rnns-3f06d7653a85
# Why recurrent
RNNs are called ==recurrent== because they perform the same task for every element of a sequence, with the output being depended on the previous computations. 

Another way to think about RNNs is that they have a “memory” which captures information about what has been calculated so far.

# Architecture and components 
![RNN-1.png|400](/img/user/_assets/images/RNN-1.png)
$$h(t)=f(Ux(t)+Wh(t−1))$$
- $h(t)$ is the hidden state at time t
- $x(t)$ is the input at time t
- $U$, $W$, and $V$ are weights for input-to-hidden connections, hidden-to-hidden recurrent connections, and hidden-to-output connections, respectively.
- The function f is taken to be a non-linear transformation such as tanh, ReLU.
- $o(t)$ illustrates the output of the network and is also often subjected to non-linearity
- recurrent: the output does not only depend on the input but also the hidden states 

### Forward propagation

![](/img/user/_assets/images/RNN-2.png)
where the tanh can be ReLu too and the softmax can be sigmoid too.
### Back propagation
The gradient computation involves performing a forward propagation pass moving left to right through the graph shown above followed by a backward propagation pass moving right to left through the graph. 


# Different types of RNN
![Pasted image 20240825204844.png|500](/img/user/_assets/images/Pasted%20image%2020240825204844.png)

# Variations of RNN
- [[StudyNotes/Long Short Term Memory\|Long Short Term Memory]]
- [[_staging/Grated Recurrent Unit\|Grated Recurrent Unit]]
- Bidirectional RNN: 
	- a RNN that processes data in both forward and backward directions
	- helpful in [[StudyNotes/Natural Language Processing\|Natural Language Processing]]
	- disadvantage: need the entire sequence of data before making any predictions
- Deep RNNs
	-  an extension of standard RNNs that consist of multiple layers of RNN units stacked on top of each other
	- can learn complex representations
	- computational complexity


# Pros & Cons
- Pros: handle long-range dependency
- Cons: inefficient, gradient vanishing/exploding
	- [[StudyNotes/Transformer\|Transformer]] may work as a better alternative

