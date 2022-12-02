---
{"dg-publish":true,"permalink":"/mathcards/linear-time-invariant-lti-systems/"}
---

# Linear Time-Invariant (LTI) systems
The linear time-invariant (LTI) system is an example of linear shift-invariant systems, with the stimulus $s(t)$ and the response $r(t)$.
### The LTI systems have:
- linearity = superposition principle
$$ f_{LTI}(\sum s_i(t)) = \sum f_{LTI}(s_i(t)) = \sum r_i(t)$$
- time-invariance = output is independent of time shift
since: $$r(t)=f_{LTI}(s(t))$$
then: $$r(t-t_0) = f_{LTI}(s(t-t_0))$$


# Eigenfunctions of LTI systems
### Eigenfunction 
It is similar to eigenvectors: it is the eigenfunctions in a function space.
$$Df = \lambda f$$ where f is the eigenfunction of D.
### Eigenfunctions of LTI systems are sin and cos functions
If $s_E(t)$ is the eigenfunction and H is the eigenvalue, there should be the [[Mathcards/Convolution\|Convolution]]: $$s_E(t) * h(t) = H s_E(t)$$
then the solution is:
$$s_E(t) = e^{i\omega t} = e^{i2\pi ft} = cos(2\pi ft) + i \, sin(2\pi ft)$$

## [[Mathcards/Correlation\|Correlation]] and LTI systems
### Auto-correlation of the output signal $r$ in LTI systems (i.e. $r$ and $s$ are real-valued):
because $r(\tau) = s(\tau) \ast h(\tau)$, 
$$\varphi_{rr}(\tau) = r(\tau) \star r(\tau) =  r(-\tau) \ast r(\tau) = s(-\tau) \ast h(-\tau) \ast s(\tau) \ast h(\tau)$$
which means:
$$\varphi_{rr}(\tau) = \varphi_{ss}(\tau) \ast \varphi_{hh}(\tau)$$ (Wien-Lee Relation)
with Wiener-Lhinchin Theorem, for power spectral density:
$$|R(f)|^2 = |S(f)|^2 \ |H(f)|^2$$
### Cross-correlation between input $s$ and output $r$
$$\varphi_{sr}(\tau) = s(\tau) \star r(\tau) = s^*(-\tau) \ast r(\tau) = s(-\tau) \ast r(\tau) = s(-\tau) \ast \ s(\tau) \ast h(\tau) = \varphi_{ss} \ast h(\tau)$$
$$FT\{\varphi_{sr}(\tau)\} = FT\{\varphi_{ss} \ast h(\tau)\} $$
with Wiener-Khinchin Theorem:
$$\Phi _{sr} = |S(f)|^2 \ H(f)$$
**System identification** is based on this, i.e. to determine the $H(f)$:
The transfer function of an LTI system ($H(f)$) can be determined from the power spectrum of the input signal ($S(f)$) and the cross spectrum between input and output signals ($\Phi _{sr}$). 

# LTI system with white noise
The output of LTI system with white noise signals is:
$$\varphi _{rr}(\tau) = \varphi _{hh}(\tau) \ast \varphi _{ss}(\tau) = \varphi _{hh}(\tau) \ast N_0 \delta (\tau) = N_0 \ \varphi _{hh}(\tau) $$
with FT:
$$\Phi _{rr}(f) = N_0|H(f)|^2$$

****