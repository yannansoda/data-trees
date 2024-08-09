---
{"topic":"Modeling, DeepLearning","dg-publish":true,"permalink":"/Notes/Diffusion Model/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is diffusion model
- Diffusion models are a class of mathematical models used to describe how particles or information spread over time in a medium (e.g., physical space, social networks, etc.)
#### mathematical representation
$$ dx(t)= \sqrt{D} \, dW(t)$$
where:
- $x(t)$ is the state variable (e.g., accumulated evidence)
- $D$ is the diffusion coefficient
- $W(t)$ is a Wiener process (representing random noise)
#### key feature
- stochastic: the process is inherently random

### Application of diffusion models
#### in cognitive science
- decision-making 
	- diffusion models describe the accumulation of evidence over time as a stochastic process. The decision is made when the accumulated evidence reaches a certain threshold.
	- also see [[Notes/Drift Diffusion Model#in cognitive science\|Drift Diffusion Model#in cognitive science]]
#### in deep learning/AI
- diffusion process is useful for generative models to create new data by starting from noise and refining it into a meaningful output
	- forward process
		- it is a diffusion process where noise is incrementally added to the data at each step  
		- this gradual corruption transforms the data into pure noise
	- reverse process 
		- it is a diffusion process that denoises the data step by step
		- this reverses the noise addition and reconstructs the original or new data from the noisy latent representation
- examples
	- latent diffusion model
		- it operate in a compressed latent space instead of the original data space, making them computationally more efficient while still producing high-quality outputs
		- the diffusion process (i.e., adding and then reversing noise) is applied within this latent space, allowing the model to learn and generate high-quality data with less computational expense
	- stable diffusion model
		- a specific implementation of a latent diffusion model
		- a type of LDM designed for tasks like generating images, text, or other types of data from prompts or initial inputs


### Diffusion model vs. Drift diffusion model
The [[Notes/Drift Diffusion Model\|Drift Diffusion Model]] is an extension of the diffusion model, specifically tailored for modeling decision-making processes and with a drift component to the diffusion process. 



