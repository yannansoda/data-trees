---
{"dg-publish":true,"permalink":"/notes/fourier-transform/"}
---

# Fourier transformation
It transforms between time and frequency domains.
$$h(t) \circ - \bullet H(f) $$
### Transfer function
$$H(f) = \int h(t) e^{-i2\pi ft} dt$$
### Impulse response
$$h(t) = \int H(f) e^{i2\pi ft} df$$
For general functions, equivalent descriptions in time and frequency domains are based on Fourier and inverse Fourier transformations.
### Fourier transformation
$$S(f) = \int s(t) e^{-i2\pi ft} dt = FT\{s(t)\}$$
### Inverse Fourier transformation
$$s(t) = \int S(f) e^{i2\pi ft} df = FT^{-1}\{S(f)\}$$
(notice that the $exp$ with different numbers!)

### Use in [[Computational Neuroscience\|Computational Neuroscience]]
the impulse response is important in experimental approach to system identification: Apply sine stimuli and measure $S(f)$,
i.e., gain and phase, for all frequencies $f$, then you can get $s(t)$.

# Special Cases
### FT of sine & cosine
- the FT of cosine functions are real-valued
-  the FT of sine functions are purely imaginary
> [!Notice]  Proof
$$\omega = 2\pi f$$
$$FT\{\delta (t-t_0)\} = \int_{-\infty}^{\infty} \delta(t-t_0) e^{-i\omega t}dt = e^{-i\omega t_0}$$
$$FT\{e^{-i\omega_0 t}\} = \int_{-\infty}^{\infty} e^{-i\omega_0 t}e^{-i\omega t}dt = \int_{-\infty}^{\infty} e^{-i(\omega+\omega_0)t} = 2\pi \delta (\omega - \omega_0)$$
Euler´s formula:
$$\cos(\omega_0 t) =\frac{1}{2}\left( e^{i\omega_0 t}+e^{-i\omega_0 t}\right)$$
$$\sin(\omega_0 t) =\frac{1}{2i}\left( e^{i\omega_0 t}-e^{-i\omega_0 t}\right)$$
then,  $$FT\{\cos(\omega_0 t)\} 
= \int_{-\infty}^{\infty} \cos(\omega_0 t)e^{-i\omega t}dt \\
= \frac{1}{2} (( \int_{-\infty}^{\infty} e^{i\omega_0 t}e^{-i\omega t}dt+
\int_{-\infty}^{\infty} e^{-i\omega_0 t}e^{-i\omega t}dt) \\
= \frac{1}{2} ( \int_{-\infty}^{\infty} e^{-i(\omega-\omega_0)t}dt+
\int_{-\infty}^{\infty} e^{-i(\omega+\omega_0) t}dt) \\
= \pi (\delta (\omega+\omega_0)+\delta(\omega-\omega_0))$$
Similar for sine (purely imaginary):
$$FT\{\sin(\omega_0 t)\} = i\pi\left(\delta (\omega+\omega_0)-\delta(\omega-\omega_0) \right)$$

### Difference of Gaussians (DoG) 
A classical model for a radially symmetrical center-surround receptive field is a Difference of Gaussians (DoG), where two Gaussians with different widths are subtracted from each other (Mexican hat model). 

### FT of [[Notes/Dirac Delta function\|Dirac Delta function]]
$$s(t)*\delta (t) = \int s(\tau) \delta(t-\tau)d\tau = s(t)$$
$$\delta (f- f_0) = \int e ^{-i 2 \pi(f-f_0)t} \ dt$$
$$FT\{\delta (t-t_0)\} = \int \delta (t-t_0) e^{i2\pi ft}dt = e^{-i2\pi ft_0}$$
$$FT\{e^{-i2\pi f_0t}\} = \int e^{-i2\pi f_0t} e^{i2\pi ft}dt = \int e^{-i2\pi (f-f_0)t} dt= \delta (f- f _0)$$


### FT of a Gaussian kernel
With a Gaussian $G (x; \sigma)=\frac{1}{\sqrt {2 \pi} \sigma} \ exp (- \frac {x^2}{2 \sigma ^2})$ :
$$FT \{G(x; \sigma) \} = \frac{1}{\sqrt {2 \pi}} \ exp( - \frac{\sigma ^2 \omega ^2}{2})$$
- So the Fourier transform of the Gaussian function is again a Gaussian function, but now of the frequency $\omega$.
- A smaller kernel in the spatial domain gives a wider kernel in the Fourier domain, and vice versa.




# FT and [[Notes/Convolution\|Convolution]]
Convolution in time domain can be converted to multiplication in frequency domain by Fourier transformation. 
$$r(t) = s(t)*h(t) \circ - \bullet R(f) = S(f)H(f)$$
$$\int |s(t)| ^ 2 dt  \circ - \bullet \int |S(f)|^2 df$$
