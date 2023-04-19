---
{"dg-publish":true,"permalink":"/sequential-probability-ratio-test/"}
---


The Sequential Probability Ratio Test is a likelihood ratio test for determining which of two hypotheses is more likely. It is appropriate for sequential independent and identially distributed (iid) data.

Assume we take a series of measurements, from time 1 up to time t ($m_{1:t}$), and that our state $s$ is either +1 or -1. To figure out what the state is given our measurements, we cam use a log likelihood ratio $L_T$.
$$
\begin{align*}

L_T &= log\frac{p(m_{1:t}|s=+1)}{p(m_{1:t}|s=-1)}

\end{align*}

$$
Since our data is independent and identically distribution, the probability of all measurements given the state equals the product of the separate probabilities of each measurement given the state ($p(m_{1:t}|s) = \prod_{t=1}^T p(m_t | s)$). We can substitute this in and use log properties to convert to a sum.
  
$$
\begin{align*}

L_T &= log\frac{p(m_{1:t}|s=+1)}{p(m_{1:t}|s=-1)}\\

&= log\frac{\prod_{t=1}^Tp(m_{t}|s=+1)}{\prod_{t=1}^Tp(m_{t}|s=-1)}\\

&= \sum_{t=1}^T log\frac{p(m_{t}|s=+1)}{p(m_{t}|s=-1)}\\

&= \sum_{t=1}^T \Delta_t

\end{align*}
$$
  

where $\Delta_t = log\frac{p(m_{t}|s=+1)}{p(m_{t}|s=-1)}$.

If $L_T$ is positive, then the state $s=+1$ is more likely than $s=-1$, and vice versa.



# Drift Diffusion Model
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
as claimed. The log-likelihood ratio $L_t$ is a biased random walk --- normally distributed with a time-dependent mean and variance. This is the **Drift Diffusion Model**.
The $b$ is a drift component, and the $c$ is a diffusion component.