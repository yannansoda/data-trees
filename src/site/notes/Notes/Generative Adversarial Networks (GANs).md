---
{"topic":"DeepLearning","dg-publish":true,"permalink":"/Notes/Generative Adversarial Networks (GANs)/","dgPassFrontmatter":true,"noteIcon":""}
---

## What is GAN?
= A framework to train generative models via adversarial process.
### Architecture
  - **Generator (G)**
	  - Creates fake data from random noise
	  - Takes noise vector z (sampled from e.g., Gaussian) → outputs synthetic data
  - **Discriminator (D)**
	  - Tries to distinguish real data from fake data
	  - Takes data (real or fake) → outputs probability of being real
## How it works
- ### "adversarial"
	- G tries to fool D by producing realistic samples
	- D tries to correctly classify real vs fake
	- Both networks train simultaneously in a minimax game
### Training Process
1. Sample real data batch
2. Sample noise batch
3. Train D on real and fake data
4. Train G to fool D
5. Repeat until convergence
### Loss Functions
- Discriminator loss:
$$
  L_D = - \mathbb{E}_{x \sim p_{data}}[\log D(x)] - \mathbb{E}_{z \sim p_z}[\log(1 - D(G(z)))]
$$
- Generator loss:
$$
  L_G = - \mathbb{E}_{z \sim p_z}[\log D(G(z))]
$$
## Challenges
- Training instability
- Mode collapse (generator produces limited diversity)
- Balancing G and D power
