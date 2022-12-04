---
{"dg-publish":true,"permalink":"/notes/ica/"}
---

ICA assumes a source vector s with components si that are mutually independent. The sources are not observed directly, but linear combinations of the sources x are given such that

$$
x = As
$$

where A is a N x M scalar matrix. The columns of A are called the basis functions.

The goal of ICA is to find the basis functions by adaptation or learning given only the observed data x. 
During the adaptation process a cost function such as the mutual information function is minimized by using an adaptation rule. 
Once the minimum is achieved, the sources s; will be as linearly independent as possible.

The many variants of the ICA adaptation algorithm can be loosely categorized into parametric and non-parametric algorithms.

- the parametric approach assumes an adaptive or nonadaptive prior distribution on the source densities p(s).
- the nonparametric approach tries to approximate the under- lying statistics using cumulants up to 4th order.