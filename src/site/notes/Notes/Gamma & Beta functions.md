---
{"dg-publish":true,"permalink":"/notes/gamma-and-beta-functions/"}
---


# Gamma function
*definition:*
$$\Gamma(x) = \int ^{\infty} _0 e^{-t} \ t^{x-1} \ dt 
\ \ \ (x > 0)$$
- special cases:
$$ \Gamma(1) =1$$
$$\Gamma(0.5) = \sqrt \pi$$
- For any $n > 0$,
$$\Gamma (n+1) = n \ \Gamma (n) = (n) !$$
- Other forms:
$$\Gamma(\alpha, \beta) = f(\lambda) = \lambda ^{\alpha -1} e^{-\beta \lambda}$$

## Beta function
*definition:*
$$B(x, y) = \int _0 ^1 t^{x-1} (1-t) ^{y-1} dt 
\ \ \ (x>0, y>0)$$
- beta distribution (of t):
$$p(t | x, y) = beta(t | x, y) = t^{x-1} (1-t) ^{y-1} / B(x,y)$$
where B(x, y) is a beta function as the normalizer.

- relations with Gamma function:
$$B(\alpha, \beta) = \frac{\Gamma (\alpha) \Gamma (\beta)}{\Gamma(\alpha + \beta)}$$