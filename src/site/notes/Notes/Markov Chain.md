---
{"topic":"Math","dg-publish":true,"permalink":"/Notes/Markov Chain/","dgPassFrontmatter":true,"noteIcon":""}
---

## Definitions
- **state**
	- The state of a Markov chain at time t is the value of X_t
- **state space**
	- The state space of a Markov chain, S, is the set of values that each X_t can take.
- **trajectory**
	- A trajectory of a Markov chain is a particular set of values for X0,X1,X2, ...
- **Markov property**
	- Markov property: conditioned on the present state of the world, the past is independent from the future.
{ #b013c4}

	- i.e. X_{t+1} depends on only X_t, but not X_{t-1}, ..., X1, X0.
	- mathematically: $$P(X_{t+1} = s | X_t=s_t, X_{t-1}=s_{t-1}, ... X_0=s_0) = p(X_{t+1}=s | X_t=s_t)$$
## Transition matrix
- illustration of transition matrix: [source of the figure](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.stat.auckland.ac.nz/~fewster/325/notes/ch8.pdf)
![[Pasted image 20240328092446.png \| 500]]
- characteristics of the transition matrix
	- the matrix is a square matrix (N x N)
	- the rows should each sum to 1 (sum of all probabilities to the all possible state from a single state)
	- the columns do not in general sum to 1
- t-step transitions theorem
	- the t-step transition probabilities are given by: $$P(X_t=j | X_0=i) = (P^t)_{ij}$$
## Types of Markov model
Models of the Markov property that estimate 
	- discrete hidden variables:  Hidden Markov Models (HMM)
	- continuous hidden variables (with Gaussian probability): [[Notes/Kalman model\|Kalman model]]

# Hidden Markov Models (HMM)
![Screenshot 2023-03-21 at 16.15.39 1.png|700](/img/user/_assets/images/Screenshot%202023-03-21%20at%2016.15.39%201.png)