---
{"topic":"Math, Statistics","dg-publish":true,"permalink":"/Notes/Kernel Function/","dgPassFrontmatter":true,"noteIcon":""}
---

A kernel is a positive function $K(x;h)$ which is controlled by the bandwidth parameter $h$. Given this kernel form, the density estimate at a point $y$ within a group of points $x_i; i=1 ...N$ is given by:
$$p \kappa(y) = \sum^N K(y-x_i; h)$$
 

### Types of Kernels

> [!source]
>  https://scikit-learn.org/stable/modules/density.html

![](/img/user/_assets/images/kernel-density-2.png)