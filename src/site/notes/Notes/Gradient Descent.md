---
{"dg-publish":true,"permalink":"/Notes/Gradient Descent/","noteIcon":""}
---

-- to minimize cost function using derivatives 

## Gradient descent in Neural networks
- use forward-propagation to calculate the values of each layer
- use back-propagation to calculate the derivatives 
- example of a two-layer logistic regression neural network by Andrew Ng:
![Pasted image 20230310114003.png](/img/user/assets/images/Pasted%20image%2020230310114003.png)

## batch gradient descent vs. stochastic gradient descent
- different purposes: stochastic ones can avoid local minimum 
- different ways to update weights
![/assets/images/artificial-nn2.png](/img/user/assets/images/artificial-nn2.png)

>[!Note] One of the popular algorithms is Adam:
Adam is an optimization algorithm that can be used instead of the classical stochastic gradient descent procedure to update network weights iterative based in training data.