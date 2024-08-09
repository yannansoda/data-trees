---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Distance between two distributions/","dgPassFrontmatter":true,"noteIcon":""}
---


### Total Variation Distance (TVD, or variation distance or statistical distance) 
= the maximum absolute difference in probabilities assigned to any single event by the two distributions.
$$ d_{TVD}(P, Q) = \frac{1}{2} \sum_x |P(x) - Q(x)|$$, where x ranges over all possible values in the sample space
- range in [0, 1], where 1 = no events in common
- symmetric
- robust to outliers and can capture the largest discrepancy between discrete/continuous distributions

### Wasserstein Distance (Earth Mover's distance or Kantorovich-Rubinstein distance) 
= the minimum amount of work needed to transform one distribution into the other, where "work" is defined in terms of the cost of moving mass from one point to another.
$$W_p(P, Q) = \left( \inf_{\gamma \in \Pi(P, Q)} \int_{\mathcal{X} \times \mathcal{X}} d(x, y)^p d\gamma(x, y) \right)^{\frac{1}{p}}
$$
- range in [0, inf/diameter of the support of the distributions]
- useful for comparing distributions with complex shapes or high-dimensional data

### Hellinger Distance
= the similarity between two probability distributions by comparing the square root of the difference between the square roots of the probability densities.
$$ H^{2}(P, Q) = \frac{1}{2} \sum_x (\sqrt{P(x)} - \sqrt{Q(x)})^2$$
- range in [0, 1]
- sensitive to differences in the tails of distributions

### Kullback-Leibler Divergence (KL Divergence)
see [[Notes/Information theory and Entropy in Neuroscience#Kullback-Leibler Divergence\|Information theory and Entropy in Neuroscience#Kullback-Leibler Divergence]]
- range in [0, inf]
- not symmetric

### Jensen-Shannon Divergence
= a symmetrized version of KL divergence that measures the similarity between two distributions by averaging their KL divergences from the average of the two distributions.
$$ D_{JS}(P||Q) = \frac{1}{2} D_{KL}(P||M) - \frac{1}{2} D_{KL}(Q||M)$$ where $M=\frac{1}{2}(P+Q)$ is the average of the two distributions
- range in[0, log(2)]
- symmetric
- captures both the divergence and convergence between distributions.