---
{"dg-publish":true,"permalink":"/notes/convolution/"}
---

# Convolution $\ast$
$$r(t)  = s(t) * h(t) = \int s(\tau)h(t-\tau)d\tau$$

# Convolution in [[Index/Computational Neuroscience\|Computational Neuroscience]]:
- In image processing, the retina functions as linear filters (receptive fields) that involves in convolutions.
- For example, a low-pass filter can blur the image, i.e. remove high-contrast and high spatial patterns. 
> [!example] Example - Gaussian kernel
> - 1-D Gaussian kernel:
> $$G_{1D} (x; \sigma)=\frac{1}{\sqrt {2 \pi} \sigma} \ exp (- \frac {x^2}{2 \sigma ^2})$$
> - N-D Gaussian kernel:
> $$G_{ND} (x; \sigma)=\frac{1}{ (\sqrt {2 \pi} \sigma) ^N} \ exp (- \frac {x^2}{2 \sigma ^2})$$