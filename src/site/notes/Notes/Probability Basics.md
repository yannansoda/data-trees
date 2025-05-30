---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Probability Basics/","dgPassFrontmatter":true,"noteIcon":""}
---


### Joint distribution
The joint distribution of two random variables $X$ and $Y$:
$$p(x, y) = p(X=x, Y=y)$$

### Marginal distribution
The Marginal distribution of $X$ is summing over all possible states of $Y$: 
$$ p(X=x) = \sum_y p (X=x, Y=y)$$
This is also called Sum rule / The rule of total probability.

### Conditional joint
$$p(X, Y|Z) = p(X|Z)p(Y|Z) $$
### Product rule 
$$
p(A, B) = p(A | B) p(B) = p(B | A) p(A)
$$
### Chain rule
$$
p(A_1, A_2, A_3, ..., A_n) = p(A_1) \times p(A_2|A_1) \times p(A_3|A_1, A_2) \times ... \times p(A_n|A_1, A_2, ..., A_{n-1}) 
$$
> Note that [[Notes/Markov Chain\|Markov chain]] can be regarded as a simplified version of the chain rule, i.e. predict by ignoring all previous events but the last one(s), so that $p(A_n| A_1, .. A_{n-1}) \approx p(A_n | A_{n-1})$
- application for multiple variables:
$$
p(A|B, C) p(B | C) = p(B|A, C) p(A|C)
$$
derivation:
$$
p(A|B, C) = p(A, B, C) / p(B, C) 
$$
with 
$$
p(A, B, C) = p(B|A, C) p(A|C) p(C), \ \ p(B, C) = p(B|C)p(C)
$$