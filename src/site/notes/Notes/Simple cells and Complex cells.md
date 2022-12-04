---
{"dg-publish":true,"permalink":"/notes/simple-cells-and-complex-cells/"}
---


# Simple cells vs Complex cells
| | simple cells| complex cells |
| --- | --- | --- |
| feature | with excitatory and inhibitory regions in RFs | with no inhibitory and excitatory regions in RFs|
| example | the cell responds to a horizontal slit and responds higher when the slit is positioned somewhere in RFs; similarly, the cell will respond to drifiting gratings | the cell responds to a horizontal slit anyway, the position does not matter; similarly, the cell will not respond to drifting gratings|
| orientation selectivity (e.g. is the slit horizontal?) | Y | Y |
| spatial-frequency selectivity | Y | Y |
| spatial-phase selectivity | Y | N (**phase invariance**)|
| model | Gabor filter | combination of simple cell responses |

# Simple cell model: Gabor filter (linear)
A Gabor filter can be viewed as a sinusoidal signal of particular frequency and orientation, modulated by a Gaussian wave.
Real-valued Gabor filter in the space domain: 
$$G(x,y) = \frac{1}{2 \pi \sigma_x \sigma_y} exp（- \frac {x^2} {2 \sigma_x^2} - \frac {y^2} {2 \sigma_y^2}）cos(kx - \Phi)$$
Simple cell receptive fields (e.g. in cat striate cortex) are often found to be well fit by Gabor functions. 

If including the orientation angle $\theta$ and phase $\varphi$:
$$G(x,y,[\varphi, \theta]) = \frac{1}{2 \pi \sigma_x \sigma_y} exp(-\frac{x^2}{2 \sigma_x^2}-\frac{y^2}{2 \sigma_y^2})  \cos(k(x\cos(\theta)+y\sin(\theta)) - \varphi)$$
- with $\varphi = k \pi$, G is an even-symmetrical Gabor 
- with $\varphi = k \pi /2$, G is an odd-symmetrical Gabor 

### Complex cell model: Quadrature pair of simple cell models
To model the phase-invariance, the model of complex cells is the summation of responses of simple cells with phase difference $\pi/2$, which is the quadrature pair of simple cell models.
For example, Pollen & Ronner (1981) found neighboring simple cells in cat primary visual cortex with similar orientation and spatial-frequency tuning, but 90 degree phase shift. 