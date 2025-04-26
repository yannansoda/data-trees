---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Representational Similarity Analysis/","dgPassFrontmatter":true,"noteIcon":""}
---


Representational Similarity Analysis (RSA) is an approach that could help us understand the internal representation of deep learning neural network.

#### Why "Representational" 
 
- representation matters: neural networks should be able to learn representations of latent variables without human labelled data 
- invariance matters: representations should be invariant - that is what helps supervised learning
	 ![Pasted image 20230425105603.png|300](/img/user/_assets/images/Pasted%20image%2020230425105603.png)

#### RSA can determine similarity 
- RSA is a way of determining how similar the representations of different stimuli are to each other
- If a network has invariant stimuli, then RSA should show that objects from the same category are represented in a similar manner regardless of how they are transformed (e.g. orientation, location, etc.
- Representational similarity matrix
 ![Pasted image 20230425104459.png|500](/img/user/_assets/images/Pasted%20image%2020230425104459.png)