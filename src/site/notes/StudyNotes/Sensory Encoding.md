---
{"topic":"CompNeuro","dg-publish":true,"permalink":"/StudyNotes/Sensory Encoding/","dgPassFrontmatter":true,"noteIcon":""}
---


# Coding mechanisms & principles

### Receptive field 
= the field in space and time of the "sensory surface"
### Tuning 
= the dependency of neuron's response to stimulus features

	e.g. Hubel and Wiesel (1962): simple cells

# Population coding
### Sparse coding 
= how many neurons are involved in coding one variable
	e.g. grandmother cell (Gross, 2002). = only one neuron ~ complex features => super sparse
### Population coding 
= more than one neuron are involved in coding one variable
- each cell has a preferred value (e.g. direction)
- overlapping cosine tuning curves (i.e. population vector)
- robust = removal of a few cells does not harm
=> The population code is the vector sum of the preferred direction $p_i$ weighted by response $f_i$ (Georgopoulos, Schwartz, & Kettner, 1986):

$$
\vec{x} = \sum{f_i \ \  \vec{p}_{\,i}}
$$

# Efficient coding 
= neural information processing (especially in sensory systems) should be adapted to the environment and input statistics
### information theory (Shannon, 1948) 
(also check  [[StudyNotes/Information theory and Entropy in Neuroscience\|Information theory and Entropy in Neuroscience]])
	- entropy = sum of information from each message $m$ within an ensemble $M$
		- $$ H(M) = - \sum{p(m)\  log_2\ p(m)} $$
		-  **most efficient = maximal entropy = all messages are equally likely = M is an uniform distribution**
	- mutual information = redundancy between A and B
		- conditional entropy
		- $$ H(A|B) = H(A, B) \ - H(B)$$
		- $$I(A; B) = H(A) \ - H(A|B)$$   which represents  the reduction in the uncertainty about one when we know the other.
### simplest case:  single neuron
- input distribution => transfer function => output distribution
- most efficient = the distribution of firing rates is uniform = the slope of the tranfer function is proportional to input probability
### mutiple neurons:  redundancy reduction 
- PCA
- Zero-phase component analysis
- [[StudyNotes/Independent component analysis\|Independent component analysis]]