---
{"topic":"Math","dg-publish":true,"permalink":"/StudyNotes/Statistical Description of Signals/","dgPassFrontmatter":true,"noteIcon":""}
---

# Statistical Description of Signals
Realisations of random process $S$:  Ensemble of random signals $s_k(t)$ 
For each $t$, the linear mean is :
$$E\{s(t_1)\} = \lim _{M ->\infty} \frac {1} {M} \sum
{ #M}
 _{k=1} s_k(t_1)$$
similarly and generally for any function $F$:
$$E\{F[s(t_1)]\} = \lim _{M ->\infty} \frac {1} {M} \sum
{ #M}
 _{k=1} F[s_k(t_1)]$$
### Stationary process: All ensemble averages are time invariant
i.e. $E\{F[s(t_1)]\} = E\{s(t_1 + t_0)\}$ for all $t_0$
$E\{F[s(t_1), s(t_2)]\} = E\{s(t_1 + t_0), s(t_2 + t_0)\}$ for all $t_0$
...
Therefore, the mean of a stationary process is:
$$E\{s(t_1)\} = E\{s(t)\} = m_s$$
The autocorrelation function of a stationary process:
$$\varphi _{ss} (\tau) = E\{s(t)s(t + \tau)\}$$

### Ergodic process
"Ergodic" means the same behaviour averaged over time as averaged over the space. So, an ergodic process show time averages equal to ensemble averages.
