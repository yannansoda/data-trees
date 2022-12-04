---
{"dg-publish":true,"permalink":"/notes/random-variables-and-probability-distributions/"}
---

# Discrete variables
## Probability function

For a discrete variable X that can take values from ${a_1, a_2, ...}$, there is a probability function for X:

$$p_i = P(X = a_i) \\ \\ (i = 1, 2, ...)$$

There are two major types of distributions for discrete variables (based on $p_i$): Binominal distribution, and Poisson distribution.

## - Binominal distribution


$$X \sim B(n, p)$$

$$p_i = b(i; n, p) = \tbinom{n}{i} p^i (1-p) ^{n-i}$$
> example: observe $X$ times of heads when flipping coins for N times. Then X=1, 2, ..., N follows this distribution.

- Mean
$$\bar{X} = np$$
- Variance
$$
Var(X) = np(1-p)
$$
>[!important] Bernoulli distribution
>The Bernoulli distribution is a special case of the binomial distribution with $n=1$. 
>- Mean $\bar{X}=p$
>- Var(X) = p(1-p)


## - Poisson distribution

$$X \sim P(\lambda)$$

$$P(X=i) = e^{- \lambda} \frac{\lambda ^i}{i!}$$

It always works when X represents the number of events that happen within a temporal or spatial domain.

## Binominal → Poisson

Poisson is an extreme case of binominal distribution:

for $X \sim B(n, p)$, when n is large & p is small & np = \\lambda is not too large, then $X \sim P(\lambda)$.

-------
# Continuous variables
## Probability density function (PDF)

For continuous variables, probability density functions are more useful than cumulative distribution functions.

For a continuous variable X with its CDF F(x), there is a probability density function of x:

$$f(x) = F'(x)$$

The probability density function has 3 features:

$$f(x) \geq 0$$

$$\int \_ {-\infty} ^{\infty} f(x) dx =1$$

$$P(a \leq X \leq b) = F (b) - F(a) = \int _a ^b f(x) dx$$

(The PDF's analog for discrete variables is probability mass function. )

There are several major types of distributions for continuous variables (based on PDF):

## - Normal distribution


$$X \sim N (\mu, \sigma ^2)$$

$$f(x) = \frac{1}{\sqrt {2 \pi }\sigma} e^{ - \frac{(x-\mu)^2}{2\sigma ^2}}$$

## - Exponential distribution


$$f(x) = \lambda e^{-\lambda x} \ \ (x>0)$$

## - Weibull distribution

The exponential distribution is a special case of the Weibull distribution with \\alpha = 1.

PDF:

$$f(x) = \lambda \alpha x^{\alpha-1} e ^{-\lambda x^\alpha} \ \ (x>0)$$

CDF:

$$F(x) = 1 - e ^{\lambda x ^ \alpha}$$

## - Uniform distribution


$$f(x) = \frac{1}{b-a} \ \ (a \leq x \leq b)$$