---
{"dg-publish":true,"permalink":"/notes/dirac-delta-function/"}
---

# Dirac Delta function $\delta (x)$**
Such a function satisified:
1. when $x=+\infty$, $\delta (x) = +\infty$,  when $x=0$, $\delta (x)=0$
2. $\int_{-\infty} ^{+\infty} \delta (x)dx = 1$

### Most important things you should know for the Delta function
- A Dirac Delta function has "sifting property":
$$\int f(y) \delta (x-y) dy = f(x)$$
looks quite like convolution, right?
- The Dirac Delta function can be given as [[Notes/Fourier Transform\|Fourier Transform]] as:
$$\delta (t) = FT \{ 1 (t) \} = \int e^{-i2 \pi ft} dt$$
- Dirac pulse train: Train of equidistant $\delta$ pulses in time domain corresponds to train of equidistant $\delta$ pulses in frequency domain
$$\sum \delta (t-n)  \circ - \bullet \sum \delta (f-n)$$