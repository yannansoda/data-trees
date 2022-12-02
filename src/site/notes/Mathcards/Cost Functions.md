---
{"dg-publish":true,"permalink":"/mathcards/cost-functions/"}
---

### Cost functions
- A cost function determines the "cost" (or penalty) of estimating $\hat{x}$ when the true or correct quantity is really $x$.
- This is essentially the cost of the error between the true stimulus value $y_i$ and our estimate $f(x_i)$.
- cost function formula
$$
J(\theta) = \frac{1}{m} \sum ^m L (f(x_i), y_i)
$$
where $L$ is the loss function.
- Cost vs. Loss: ==loss== applies to a single training sample; ==cost== is the mean of summed loss.

### Forms of cost functions
Note that the error can be defined in different ways:

$$\begin{eqnarray}
\textrm{Mean Squared Error} &=& (x - \hat{x})^2 \\ 
\textrm{Absolute Error} &=& \big|x - \hat{x}\big| \\ 
\textrm{Zero-One Loss} &=& \begin{cases}
                            0,& \text{if } x = \hat{x} \\
                            1,              & \text{otherwise}
                            \end{cases}
\end{eqnarray}
$$
> - In ML, Mean Squared Error is commonly used as the cost function, but with an extra division by 2, which "is just meant to make later partial derivation in gradient descent neater" :
> $$
J(\theta) = \frac{1}{2m} \sum ^m (\hat{x_i} - x_i)^2
> $$
> - Be careful about Absolute Error or Mean Absolute Error (MAE). Compared to MSE, it does not penalize large errors. But if your loss is just proportional to the size of error, then maybe MAE is better.

### Cost function with regularization
When you choose [[DataScience/Regularization\|regularization]], a regularization term will be added to the cost function.
for linear regression:

$$
J(\theta) = \frac{1}{2m} \sum_i ^m (\hat{x_i} - x_i)^2 + \frac{\lambda}{2m} \sum_j^n \theta_j ^ 2 
$$
for logistic regression:
$$
J(\theta) = \frac{1}{m} \sum ^m ( -y_i log(f(x_i)) - (1-y_i)log(1 - f(x_i))) + \frac{\lambda}{2m} \sum_j^n \theta_j ^ 2 
$$
where $j$ represents the $j$th feature. 

Increasing the regularization parameter $\lambda$ ($\lambda$ >0) reduces overfitting by reducing the size of the parameters.  For some parameters that are near zero, this reduces the effect of the associated features.

### Loss and cost for logistic regression
> MSE is not proper because the cost function would not be convex.

loss function $L(f(x_i), y_i)$:
$$
 y_i = 1: L = -log(f(x_i))
$$
$$
 y_i = 0: L = -log(1 - f(x_i))
$$

Combined the above formula together, we get the simplified cost function for logistic regression:
$$
 L = -y_i log(f(x_i)) - (1-y_i)log(1 - f(x_i))
$$

then the cost function with full form (also used in [[Mathcards/Maximum likelihood estimation\|Maximum likelihood estimation]] for logistic regression):
$$
J(\theta) = \frac{1}{m} \sum ^m ( -y_i log(f(x_i)) - (1-y_i)log(1 - f(x_i)))
$$

### Loss and cost for Softmax
What is Softmax: [[ML/Artificial Neural Networks#^6ef895\|Artificial Neural Networks#^6ef895]]

The loss function associated with Softmax, the cross-entropy loss, is:
$$
\begin{equation}
  L(\mathbf{a},y)=\begin{cases}
    -log(a_1), & \text{if $y=1$}.\\
        &\vdots\\
     -log(a_N), & \text{if $y=N$}
  \end{cases} \tag{3}
\end{equation}
$$
Only the line that corresponds to the target contributes to the loss, other lines are zero:
    $$\mathbf{1}\{y == n\} = =\begin{cases}
    1, & \text{if $y==n$}.\\
    0, & \text{otherwise}.
  \end{cases}$$
  Cost function:
$$
\begin{align}
J(\mathbf{w},b) = -\frac{1}{m} \left[ \sum_{i=1}^{m} \sum_{j=1}^{N}  1\left\{y^{(i)} == j\right\} \log \frac{e^{z^{(i)}_j}}{\sum_{k=1}^N e^{z^{(i)}_k} }\right] \tag{4}
\end{align}
$$

where $m$ is the number of examples, $N$ is the number of outputs. This is the average of all the losses.

### Expected loss function
A posterior distribution tells us about the confidence or credibility we assign to different choices. A cost function describes the penalty we incur when choosing an incorrect option. These concepts can be combined into an *expected loss* function. 

Expected loss is defined as:

$$

\mathbb{E} \ [\text{Loss} | \ \hat{x}\ ] = \ \int L\ [\ \hat{x},x\ ] \ \odot p(x|\ \tilde{x}) dx

$$

where $L\ [ \ \hat{x}, x\ ]$ is the loss function, $p(x|\ \tilde{x})$ is the posterior, and $\ \odot$ represents the [Hadamard Product](https://en.wikipedia.org/wiki/Hadamard\_product\_(matrices)) (i.e., elementwise multiplication), and $\ \mathbb{E}\ [\ \text{Loss} | \ \hat{x}\ ]$ is the expected loss.

```
- The posterior's mean minimizes the mean-squared error.
- The posterior's median minimizes the absolute error.
- The posterior's mode minimizes the zero-one loss.
```

