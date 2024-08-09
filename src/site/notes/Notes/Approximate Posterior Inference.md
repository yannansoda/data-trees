---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Approximate Posterior Inference/","dgPassFrontmatter":true,"noteIcon":""}
---


## Why need approximate posterior inference?
Approximate posterior inference methods are essential in Bayesian statistics because exact solutions to posterior distributions are often intractable.

## Types of methods
### Grid Approximation
- Grid approximation involves discretizing the parameter space into a grid of points and evaluating the posterior probability at each point.
- It is feasible for models with a small number of parameters and when the parameter space is not too large.

**Steps:**
  1. Define a grid of possible values for the parameter(s).
  2. Compute the posterior probability at each grid point.
  3. Normalize the probabilities to ensure they sum to one.
  4. Use these probabilities to approximate summaries (mean, variance, credible intervals) of the posterior distribution.
### Laplace Approximation (Quadratic approximation)
- Laplace approximation approximates the posterior distribution with a Gaussian distribution centered at the mode (maximum a posteriori estimate) of the posterior.

**Steps:**
  1. Find the mode of the posterior distribution.
  2. Compute the Hessian matrix (second derivatives) at the mode to estimate the curvature of the log-posterior.
  3. Use the mode and the inverse of the Hessian to define a Gaussian approximation.

### Variational Inference
- Variational inference (VI) approximates the posterior distribution by finding a simpler distribution that is closest to the true posterior, measured by Kullback-Leibler (KL) divergence (see [[Notes/Information theory and Entropy in Neuroscience#Kullback-Leibler Divergence\|Information theory and Entropy in Neuroscience#Kullback-Leibler Divergence]])

**Steps:**
  1. Choose a family of distributions to approximate the posterior (e.g., Gaussian).
  2. Optimize the parameters of the chosen distribution to minimize the KL divergence to the true posterior.
### Markov Chain Monte Carlo (MCMC)
- MCMC methods generate samples from the posterior distribution by constructing a Markov chain that has the desired posterior distribution as its equilibrium distribution.
- Common Algorithms
	- **[[Notes/Metropolis-Hastings Algorithm\|Metropolis-Hastings Algorithm]]**
	     - Proposes a new sample based on a proposal distribution and accepts or rejects it based on the posterior probability.
	 - **[[Notes/Metropolis-Hastings Algorithm#Gibbs Sampling\|Metropolis-Hastings Algorithm#Gibbs Sampling]]**
	     - Samples each parameter in turn from its conditional distribution given the current values of the other parameters.

### Expectation Propagation
- Expectation Propagation is an iterative algorithm that approximates the posterior by matching moments (mean and variance) between the true posterior and a simpler distribution.
**Steps:**
  1. Approximate each factor in the posterior (e.g., likelihood, prior) with a simpler distribution.
  2. Iteratively update these approximations to minimize the KL divergence to the true posterior in a way that balances the contributions of all factors.

## Comparison between methods

| approximation methods   | pros                                                                                                                                                                               | cons                                                                                                                                                                                                  |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Grid Approximation      | simple and intuitive                                                                                                                                                               | computationally expensive for high-dimensional parameter spaces                                                                                                                                       |
| Laplace Approximation   | - simple to implement<br>- works well for unimodal, approximately Gaussian posteriors                                                                                              | - poor approximation for non-Gaussian or multi-modal posteriors<br>- requires second-order derivatives, which can be computationally expensive                                                        |
| Variational Inference   | - often faster than MCMC<br>- scales well to large datasets<br>                                                                                                                    | - the quality of the approximation depends on the chosen family of distributions<br>- may not capture all features of the true posterior, especially if the posterior is multi-modal or highly skewed |
| MCMC                    | - can handle high-dimensional and complex posterior distributions<br><br>                                                                                                          | - can be slow to converge and computationally intensive<br>- requires careful tuning of algorithm parameters                                                                                          |
| Expectation Propagation | - provides good approximations for certain types of models, especially in Bayesian machine learning<br>- can handle complex posterior distributions better than some other methods | - more complex to implement and understand<br>- may not converge or provide good approximations in all cases                                                                                          |
|                         |                                                                                                                                                                                    |                                                                                                                                                                                                       |

