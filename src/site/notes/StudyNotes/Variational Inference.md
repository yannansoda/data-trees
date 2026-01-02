---
{"topic":"Statistics, Modeling","dg-publish":true,"permalink":"/StudyNotes/Variational Inference/","dgPassFrontmatter":true,"noteIcon":""}
---


## What is Variational Inference

= a method in Bayesian statistics and machine learning for **approximating complex probability distributions**:
- Instead of trying to directly calculate a complicated posterior distribution $p(z \mid x)$ (often intractable), we pick a _simpler family_ of distributions $q_\phi(z)$ and try to find the one that is **closest** to the true posterior.

### Why use Variational Inference
- **the Bayesian context**: the marginal likelihood $p(x)$, which is needed for computing the posterior via Bayesian inference, is often intractable (cannot compute exactly)
- Variational Inference can turn inference into optimization.
## How it works
1. Choose a family of approximating distributions $q_\phi(z)$ (e.g., Gaussian with mean and variance parameters)
2. Optimize parameters $\phi$ to maximize the *Evidence Lower Bound (ELBO)*:
$$
   \mathbb{E}_{q_\phi(z)}[\log p(x \mid z)] - \text{KL}(q_\phi(z) \;||\; p(z))
$$
3. Use gradient-based methods for optimization.

## Applications
- [[StudyNotes/Variational Autoencoders (VAE)\|Variational Autoencoders (VAE)]]
- [[StudyNotes/Probabilistic Graphical Models\|Probabilistic Graphical Models]]
