---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Reinforcement learning/","dgPassFrontmatter":true,"noteIcon":""}
---


> [!Key Concepts]
> - states $s_i$ 
> - actions $a_i$
> - rewards $R$
> - discount factor $\gamma \in [0, 1]$: specifies the relevance in the present of future rewards.
> - return $G$: cumulative reward
> - policy $\pi$: a specification of how the agent acts. $\pi(a|s)$ gives the probability of taking action $a$ when in state $s$.
# Markov decision process
The core reinforcement learning approaches define the world as a Markov decision problem, which is built on hidden dynamics and optimal control.
 $$G = R_i + \lambda R_{i+1} + \lambda^2 R_{i+2} + \lambda^3 R_{i+3}+ ... $$
	 ...until termination.

# State-action value function (Q function)
- The goal of reinforcement learning is to choose a policy $\pi (s)=a$ that will tell us which action to take in state $s$ so as to maximize the expected return. 
- Q function specifies how good it is for an agent to perform a particular action in a state with a policy $\pi$.
- the state-action value function Q(s, a) = Return, if you
	- start in state $s$
	- take action $a$ (once, to $s'$) 
	- then behave optimally after that
the best possible return from state $s$ is $max_{a} \ Q(s, a)$
- Bellman equation:
$$
Q(s, a) = R(s)+\gamma \ max_{a'} \ Q(s', a')
$$
i.e. it is the sum of reward at the current state and the return from behaving optimally starting from the state $s'$.
- It helps to compute the state action value function in reinforcement learning.
# Algorithms 
![](/img/user/assets/images/reinforcement-learning-1.png)
## Upper Confidence Bound
UCB is a deterministic algorithm for Reinforcement Learning that focuses on exploration and exploitation based on a confidence boundary that the algorithm assigns to each machine on each round of exploration. These boundary decreases when a machine is used more in comparison to other machines.
> example: which Ads customers will click on
### How it works
1. At each round n, we consider two numbers for machine m:
	- N(n) = number of times the machine m was selected up to round n.
	- R(n) = number of rewards of the machine m up to round n.
2. From these two numbers we have to calculate,
	- The average reward of machine m up to round n, $$r(n) = R(n) / N(n)$$
	- The confidence interval $[r(n) — Δ(n), r(n)+Δ(n)]$ at round n with, 
$$Δ(n)= \sqrt{ 1.5 * log(n) / N(n) } $$
3. We select the machine m that has the maximum $UCB = r(n)+Δ(n)$

> Intuitive explanation
https://medium.com/analytics-vidhya/upper-confidence-bound-for-multi-armed-bandits-problem-ea5d7bc840ff

## Thompson Sampling (Bayesian Bandits)
### How it works
1. At each round n, we consider two numbers for machine m:
	- $N_i^1(n)$ = number of times the ad $i$ got reward 1 up to round n.
	- $N_i^0(n)$ = number of times the ad $i$ got reward 0 up to round n.
2. For each ad $i$, we take a random draw from the beta distribution below:
	$$
	\theta_i (n) = \beta (N_i^1 (n)+1, N_i^0 (n) + 1)	
  $$
3. We select the ad that has the highest $\theta_i (n)$


 


 
 Optimal Q function
 