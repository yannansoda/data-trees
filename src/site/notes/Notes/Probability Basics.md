---
{"topic":"Statistics","dg-publish":true,"permalink":"/Notes/Probability Basics/","dgPassFrontmatter":true,"noteIcon":""}
---

# Conditional Probability
### Multiplication 
$$
p(A, B) = p(A | B) p(B) = p(B | A) p(A)
$$
### Chain rule
$$
p(A_1, A_2, A_3, ..., A_n) = p(A_1) \times p(A_2|A_1) \times p(A_3|A_1, A_2) \times ... \times p(A_n|A_1, A_2, ..., A_{n-1}) 
$$
> Note that Markov chain can be regarded as a simplified version of the chain rule, i.e. predict by ignoring all previous events but the last one(s), so that $p(A_n| A_1, .. A_{n-1}) \approx p(A_n | A_{n-1})$
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