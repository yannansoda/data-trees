---
{"topic":"DeepLearning","dg-publish":true,"permalink":"/StudyNotes/Variational Autoencoders (VAE)/","dgPassFrontmatter":true,"noteIcon":""}
---

## What is VAE?
= A generative model that learns latent variable distributions.
- extends [[StudyNotes/Autoencoders\|Autoencoders]] with probabilistic encoding ([[StudyNotes/Variational Inference\|Variational Inference]])
- enables smooth latent space and generative capabilities
### Architecture
- **Encoder**
- **Decoder**
## How it works
1. **Encoder** maps input $x$ to parameters of latent distribution $q_\phi(z|x)$ — mean $\mu$ , variance $\sigma^2$.
2. **Sampling**: Latent vector $z$ sampled from this distribution using the **reparameterization trick** (enables backpropagation through stochastic sampling): 
$$
  z = \mu + \sigma \odot \epsilon, \quad \epsilon \sim \mathcal{N}(0, I)
$$
3. **Decoder**: Reconstructs $x$ from $z$ by modeling $p_\theta(x|z)$.
### Loss Function
- ELBO (Evidence Lower Bound):
$$
  \mathcal{L}(\theta, \phi; x) = \mathbb{E}_{q_\phi(z|x)}[\log p_\theta(x|z)] - D_{KL}(q_\phi(z|x) || p(z))
$$  
- Terms:
  - Reconstruction loss: How well decoder reconstructs input.
  - KL divergence: Regularizes latent distribution $q_\phi(z|x)$ to be close to prior $p(z)$ (usually standard normal).


