---
{"topic":"Math","dg-publish":true,"permalink":"/StudyNotes/Correlation/","dgPassFrontmatter":true,"noteIcon":""}
---

# Correlation $\star$
$$\varphi_{sg}(\tau) = s(\tau)  \star g(\tau) = \int s^*(t)g(t+\tau)dt $$
> $s^*(t)$ is the conjugate function of $s(t)$. If $s(t)$ is real-valued, $s^*(t)$ is equal to $s(t)$.

# Auto-correlation function
$$\varphi _{ss} (\tau) = s(\tau) \star s(\tau) $$
due to the relation between correlation and convolution (see next section), it can be rewritten as:
$$\varphi _{ss} (\tau) = s^*(-\tau) \ast s(\tau) $$
therefore, the auto-correlation is even:
$$\varphi _{ss}(\tau) = \varphi (-\tau)$$
with maximum at $\tau = 0$:
$$\varphi _{ss}(\tau) \le \varphi _{ss}(0) = \int |s(t)|^2 dt$$
The convolution of auto-correlation is:
$$
FT\{\varphi _{ss}(\tau)\} = FT\{s^*(-\tau) \ast s(\tau) \} = S^*(f) \ S(f) = |S(f)|^2
$$
(Wiener-Khinchin Theorem)
Application: **The spectral power density is the Fourier transform of the auto-correlation function.**

Just as a correlation function provides information about the temporal relationship between two quantities, so **an autocorrelation function tells us about how a quantity at one time is related to itself evaluated at another time**.  For  white  noise,  the  stimulus  autocorrelation  function  is  0 except for one time point $\tau = 0$.