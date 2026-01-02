---
{"topic":"Math","dg-publish":true,"permalink":"/StudyNotes/Correlation and Convolution/","dgPassFrontmatter":true,"noteIcon":""}
---

# Correlation and Convolution
### Relation
$$s(\tau) \star g(\tau) = s^*(-\tau) \ast g(\tau)$$
$$s^*(\tau) \ast g(\tau) = s(-\tau) \star g(\tau)$$
### Feature comparison
| | convolution | correlation |
| --- | --- | --- |
| **commutativity** | Y | N |
| | $s(t) \ast h(t) = h(t) \ast s(t)$ | $\varphi_{sg}(\tau) = \varphi_{gs}^*(-\tau)$ |
|**associativity**| Y | N |
| | $f(t) \ast (s(t) \ast h(t)) = (f(t) \ast s(t))\ast h(t)$| Not equal |
|**distributivity**| Y | N? |
| | $f(t) \ast (s(t) + h(t)) = f(t) \ast s(t) + f \ast h(t)$| ... |