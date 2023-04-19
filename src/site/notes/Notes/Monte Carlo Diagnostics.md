---
{"topic":"Statistics, Modeling","dg-publish":true,"permalink":"/Notes/Monte Carlo Diagnostics/","dgPassFrontmatter":true,"noteIcon":""}
---

# Trace plots
# Trace rank plots 
to check whether any chain occupies a higher space than others
# R-hat
- a ratio of variances
- as total variance shrinks to average variance within chains, R-hat approaches 1:
	![](/img/user/assets/images/monte-carlo-1.png)
- No guarantees here!
# Number of effective samples (n_eff)
- "How long would the chain be, if each sample was independent of the one before it?"
- When samples are autocorrelated, you have fewer effective samples.
# Divergent transition
- a kind of rejected proposal

