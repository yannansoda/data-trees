---
{"topic":"Math","dg-publish":true,"permalink":"/Notes/Sequential Probability Ratio Test/","dgPassFrontmatter":true,"noteIcon":""}
---


# Sequential Probability Ratio Test
The Sequential Probability Ratio Test is a [[Notes/Likelihood ratio test\|Likelihood ratio test]] for determining which of two hypotheses is more likely. It is appropriate for sequential independent and identically distributed (iid) data.

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



