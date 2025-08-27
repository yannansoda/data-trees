---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Mendelian Randomization/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is Mendelian Randomization
- = a statistical and [[Notes/Causal inference#Instrumental Variables (IV)\|Causal inference#Instrumental Variables (IV)]] method used to assess causal relationships between a risk factor (exposure) and an outcome
- It is often used in biomedical and social science research
- It can be univariable or multivariable
### How does it work

#### Intuition (why "Mendelian")
Because genes are randomly assigned at conception (following Mendel's laws), they are generally independent of confounders.
-> If the genetic variants associated with the exposure are also associated with the outcome, this provides evidence for a causal effect.

The logic is similar to a “natural randomized controlled trial”.
#### Step by step
1. **Identify instrumental variables (IVs)** 
- select genetic variants (usually SNPs) that are strongly associated with the exposure.  
- mathematically, for each SNP $G$ and exposure $X$:  
$$
X = \alpha + \gamma G + \epsilon_X
$$
	
where $\gamma$ represents the effect of the SNP on the exposure.

2. **Check independence from confounders**  
- ensure that $G$ is not associated with confounders $C$ of the exposure-outcome relationship:  
$$
Cov(G, C) = 0
$$

3. **Estimate the effect of exposure on outcome**  
- use the genetic instrument to estimate the causal effect $\beta$ of the exposure $X$ on outcome $Y$:  
$$
Y = \beta X + \epsilon_Y
$$  

- since $X$ is partially determined by $G$, the instrumental variable (IV) estimate of $\beta$ can be computed as:  
$$
\hat{\beta}_{IV} = \frac{Cov(G, Y)}{Cov(G, X)}
$$

4. **Interpret causal effect**  
	- if $\hat{\beta}_{IV}$ is significantly different from zero, it suggests a causal effect of the exposure on the outcome.  
	- this estimate is less likely to be biased by confounding or reverse causation due to the random allocation of genes.
### Key Assumptions
1. **Relevance:** genetic variants are associated with the exposure  
2. **Independence:** genetic variants are independent of confounders  
3. **Exclusion restriction:** genetic variants affect the outcome only through the exposure  

### Advantages
- reduces confounding compared to observational studies  
- can help distinguish correlation from causation  
- useful for exposures that cannot be randomized experimentally  

### Limitations
- weak instruments can bias results  
- pleiotropy (genetic variants affecting multiple traits) can violate assumptions  
- requires large sample sizes for sufficient statistical power