---
{"topic":"Math, MachineLearning","dg-publish":true,"permalink":"/Notes/Neural ODE/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Source]
>[Modeling Dynamical Systems With Neural ODE: A Hands-on Guide](https://towardsdatascience.com/modeling-dynamical-systems-with-neural-ode-a-hands-on-guide-71c4cfdb84dc)
### What is Neural ODE
In [[Notes/Dynamical Systems\|Dynamical Systems]], instead of a common ODE
$$\frac{du}{dt} = f(u, t)$$, a neural ODE embeds a neural network in the ODE:
$$\frac{du}{dt} = f_{NN}(u, t)$$

### What can it help
- system identification
	- when the explicit form of the ODE is not available, we cannot use traditional ODE 
- parameter estimation

### How does it work
- first, recall how traditional ODE works:
	- it uses numerical schemes to march the system states in time (with a time-marching equation)
	- it uses numerical schemes, e.g. Euler's method
	- ![Pasted image 20240122214241.png](/img/user/assets/images/Pasted%20image%2020240122214241.png)
- how neural ODE works
	- it substitutes the unknown dynamics with neural network and combines with suitable numeral scheme to march the system
	- ![Pasted image 20240122214533.png](/img/user/assets/images/Pasted%20image%2020240122214533.png)