---
{"topic":"Math","dg-publish":true,"permalink":"/Notes/Kalman model/","dgPassFrontmatter":true,"noteIcon":""}
---


# What is Kalman Model/Filter
When the hidden variables of a [[Notes/Markov Chain\|Markov Chain]] are continuous and probability distributions are Gaussians, then the model is usually called a Kalman model. 
- When these models are used to make estimates about a given point of time, given only the past, they are generally called “filters” (Kalman filter)
- when they make estimates given both past and future, they are called “smoothers.”

# How does it work 
>[!Source] Source: [Neuromatch - The Kalman Filter](https://compneuro.neuromatch.io/tutorials/W3D2_HiddenDynamics/student/W3D2_Tutorial3.html#section-2-the-kalman-filter)

Kalman filters lie in the linear dynamical system 
$$s_t = Ds_{t-1} + w_{t-1}$$
where $D$ is a scalar that models how the estimates changes over time, and $w_t \sim \mathcal{N}(0, \sigma_p^2)$ is white Gaussian noise. 

Thus, a Kalman filter estimates a posterior probability distribution *recursively* over time using a mathematical model of the process and incoming measurements. 

The posterior mean can be expressed as:
$$
\begin{equation}
\bar{\mu}_t = (1-K) D\bar{\mu}_{t-1} + K m_t = D\bar{\mu}_{t-1} + K (m_t - D\bar{\mu}_{t-1})
\end{equation}
$$
where $K$ is known as the Kalman gain and it is a function of $t$. $m$ denotes measurements.

## Implement Kalman filter with the sum rule and product rule for Gaussians

**Step 1: Change yesterday's posterior into today's prior** 
Use the mathematical model to calculate how deterministic changes in the process shift yesterday's posterior, $\mathcal{N}(\mu_{s_{t-1}}, \sigma_{s_{t-1}}^2)$, and how random changes in the process broaden the shifted distribution:
$$
\begin{equation}
p(s_t|m_{1:t-1}) = p(Ds_{t-1}+w_{t-1} | m_{1:t-1}) = \mathcal{N}(D\mu_{s_{t-1}} + 0, D^2\sigma_{s_{t-1}}^2 +\sigma_p^2)
\end{equation}
$$
where $\sigma_p$ denotes process noise and $m$ denotes measurements.

**Step 2: Multiply today's prior by likelihood** 

Use the latest measurement to form a new estimate somewhere between this measurement and what we predicted in Step 1. The next posterior is the result of multiplying the Gaussian computed in Step 1 (a.k.a. today's prior) and the likelihood, which is also modeled as a Gaussian $\mathcal{N}(m_t, \sigma_m^2)$:

**2a: add information from prior and likelihood** 

To find the posterior variance, we first compute the posterior information (which is the inverse of the variance) by adding the information provided by the prior and the likelihood:
$$ \begin{equation}
\frac{1}{\sigma_{s_t}^2} = \frac{1}{D^2\sigma_{s_{t-1}}^2 +\sigma_p^2} + \frac{1}{\sigma_m^2}
\end{equation}
$$

Now we can take the inverse of the posterior information to get back the posterior variance.

**2b: add means from prior and likelihood** 

To find the posterior mean, we calculate a weighted average of means from prior and likelihood, where each weight, $g$, is just the fraction of information that each Gaussian provides!
$$
\begin{align}
g_{\rm{prior}} &= \frac{\rm{information}_{\textit{ }\rm{prior}}}{\rm{information}_{\textit{ }\rm{posterior}}} \\
g_{\rm{likelihood}} &= \frac{\rm{information}_{\textit{ }\rm{likelihood}}}{\rm{information}_{\textit{ }\rm{posterior}}} \\
\bar{\mu}_t &= g_{\rm{prior}} D\mu_{s_{t-1}} + g_{\rm{likelihood}} m_t
\end{align}
$$




