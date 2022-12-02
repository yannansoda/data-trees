---
{"dg-publish":true,"permalink":"/mathcards/signal-processing/"}
---


# [[Mathcards/Convolution\|Convolution]] & [[Mathcards/Fourier transformation\|Fourier transformation]]

-  Convolution & Fourier transformation
Convolution in time domain can be converted to multiplication in frequency domain by Fourier transformation. 
$$r(t) = s(t)*h(t) \circ - \bullet R(f) = S(f)H(f)$$
$$\int |s(t)| ^ 2 dt  \circ - \bullet \int |S(f)|^2 df$$


# [[Mathcards/Convolution\|Convolution]] & [[Mathcards/Correlation\|Correlation]]
-  Relation
$$s(\tau) \star g(\tau) = s^*(-\tau) \ast g(\tau)$$
$$s^*(\tau) \ast g(\tau) = s(-\tau) \star g(\tau)$$

- Feature comparison

| | convolution | correlation |
| --- | --- | --- |
| **commutativity** | Y | N |
| | $s(t) \ast h(t) = h(t) \ast s(t)$ | $\varphi_{sg}(\tau) = \varphi_{gs}^*(-\tau)$ |
|**associativity**| Y | N |
| | $f(t) \ast (s(t) \ast h(t)) = (f(t) \ast s(t))\ast h(t)$| Not equal |
|**distributivity**| Y | N? |
| | $f(t) \ast (s(t) + h(t)) = f(t) \ast s(t) + f \ast h(t)$| ... |