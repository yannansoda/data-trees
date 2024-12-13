---
{"topic":"Math","dg-publish":true,"permalink":"/assets/images/Convexity/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Source]
>https://d2l.ai/chapter_optimization/convexity.html
## Definitions
### Convex sets
- sets = basis of convexity
- definition: a set $X$ in a vector space is *convex* if for any $a, b \in X$ the line segment connecting $a$ and $b$ is also in $X$,

### Convex function
Given a convex set $\mathcal{X}$, a function $f: \mathcal{X} \to \mathbb{R}$ is *convex* if for all $x, x' \in \mathcal{X}$ and for all $\lambda \in [0, 1]$ we have
$$\lambda f(x) + (1-\lambda) f(x') \geq f(\lambda x + (1-\lambda) x').$$

## Properties
- **Jensen's inequality**
	- = the expectation of a convex function $\geq$ the convex function of an expectation
- local minima are global minima
- Below sets of convex functions are convex
- convexity and second derivatives
	- a twice-differentiable function is convex if and only if its Hessian (a matrix of second derivatives) is positive semidefinite

## Convex constraints
- can be added via the Lagrangian
- can be added with a penalty to the objective function in practice