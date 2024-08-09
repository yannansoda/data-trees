---
{"topic":"Math, Modeling, CompNeuro","dg-publish":true,"permalink":"/Notes/Drift Diffusion Model/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is drift diffusion model
- The drift diffusion model (DDM) is an extension of the [[Notes/Diffusion Model\|Diffusion Model]], specifically tailored for modeling decision-making processes.
- It adds a drift component to the diffusion process, representing a systematic bias or tendency towards one decision or another.
#### mathematical representation
$$ dx(t)= v \, dt + \sqrt{D} \, dW(t)$$
where:
- $x(t)$ is the state variable (e.g., accumulated evidence)
- $D$ is the diffusion coefficient
- $W(t)$ is a Wiener process (representing random noise)
- $v$ is the drift rate (the average rate of evidence accumulation), which determines the direction and speed of the evidence accumulation, influencing how quickly a decision is made
#### key feature
- drift: 
	- the model includes a drift term that represents the systematic accumulation of evidence in favor of one decision over another
- both stochastic and deterministic: 
	- the model combines both random fluctuations (diffusion) and systematic tendencies (drift)

### Application of drift diffusion models
#### in cognitive science
- decision marking
	- it can model binary decision-making tasks where an individual has to choose between two alternatives, and the decision is made when it reaches a pre-defined threshold

### Understand drift diffusion model with [[Notes/Sequential Probability Ratio Test\|Sequential Probability Ratio Test]]
The log likelihood ratio at a time step ($L_T$) will equal the ratio at the previous time step ($L_{T-1}$) plus the ratio for the measurement at that time step, given by $\Delta_T$:
$$
\begin{align*}

L_T = L_{T-1} + \Delta_T

\end{align*}

$$
Adding $\Delta_t$ over time gives
$$
\begin{equation}

L_T\sim\mathcal{N}\left(2\frac{\mu^2}{\sigma^2}T,\ 4\frac{\mu^2}{\sigma^2}T\right)=\mathcal{N}(bT,c^2T)

\end{equation}
$$
as claimed. 

The log-likelihood ratio $L_t$ is a biased random walk --- normally distributed with a time-dependent mean and variance. This is the **Drift Diffusion Model**.

The $b$ is a drift component, and the $c$ is a diffusion component.