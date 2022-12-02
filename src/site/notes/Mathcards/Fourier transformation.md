---
{"dg-publish":true,"permalink":"/mathcards/fourier-transformation/"}
---


## Fourier transformation
$$h(t) \circ - \bullet H(f) $$
### Transfer function
$$H(f) = \int h(t) e^{-i2\pi ft} dt$$
### Impulse response
$$h(t) = \int H(f) e^{i2\pi ft} df$$


### Fourier transformation
For general functions, equivalent descriptions in time and frequency domains are based on Fourier and inverse Fourier transformations.
$$S(f) = \int s(t) e^{-i2\pi ft} dt = FT\{s(t)\}$$
### Inverse Fourier transformation
$$s(t) = \int S(f) e^{i2\pi ft} df = FT^{-1}\{S(f)\}$$