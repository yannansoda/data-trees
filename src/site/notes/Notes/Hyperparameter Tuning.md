---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Hyperparameter Tuning/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Summary] Hyperparameter tuning is search.
# Common approaches
- Randomized Search
	- randomly try different combinations
	- narrow down the search space and identify promising hyperparameters
- Grid Search
	- try all possible combinations of hyperparameters
	- perform a more exhaustive search around the identified hyperparameters
- Coordinate-wise gradient descent
	- change them one at a time, accepting any changes that reduce testing error
- Bayesian hyperparameter optimization/AutoML
	- start with hyperparameters that worked well for similar problems

# Hyperparameter Tuning in Deep Learning
### Ordering the needs of tuning
- learning rate
	- the most important hyperparameter to tune
	- variants
		- scheduled learning rate (e.g. continuously decreasing rate, like [[Notes/Gradient Descent#Learning rate decay\|Gradient Descent#Learning rate decay]])
		- adaptive learning rate (e.g. [[Notes/Gradient Descent#Adam (Adaptive Moment Estimation)\|Gradient Descent#Adam (Adaptive Moment Estimation)]])
- momentum term (if you use [[Notes/Gradient Descent#Momentum\|Gradient Descent#Momentum]])
	- good default = 0.9
- number of hidden units
	- probably second most important
- depth (number of hidden layers)
- learning rate decay
- depending on your [[Notes/Gradient Descent#Types of Gradient Descent\|Gradient Descent#Types of Gradient Descent]], there can be also
	- mini-batch size
	- adam  ([[Notes/Gradient Descent#Adam (Adaptive Moment Estimation)\|Gradient Descent#Adam (Adaptive Moment Estimation)]])
		- always work with $\beta_1$=0.9,  $\beta_2$=0.999, $\epsilon$=1e-8
> [!Tip] 
> Unfortunately, learning rate and depth interact. In general, deeper networks need smaller learning rates. 

### How to search hyperparameters
- use Randomized Search instead of Grid Search
- use an appropriate scale for hyperparameters, e.g. log scale
- can try different strategies: Panda vs. Caviar
	 ![Pasted image 20230425100746.png|400](/img/user/assets/images/Pasted%20image%2020230425100746.png)