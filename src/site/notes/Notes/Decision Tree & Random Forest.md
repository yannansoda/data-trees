---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Decision Tree & Random Forest/","dgPassFrontmatter":true,"noteIcon":""}
---


# Decision Tree
![](/img/user/assets/images/decision-tree-1.png)
- each split part is called a "leaf"
- the splitting uses information entropy
> - How to choose what features to split on each node? 
> 	- maximize purity
> - When do you stop splitting?
> 	- when a node is a 100% one class
> 	- before the tree exceeds max depth
> 	- when improvement in purity is below a threshold score (i.e. reduced entropy/information gain)
> 	- when the sample number in a new node is below a threshold number

# Random Forest
Random forest is a `Ensemble learning` method as a `Decision tree ensemble`, which is necessary, because a single tree is sensitive to small changes of the data.
1. pick at random K dat points from the training set
2. build the decision tree associated to these K data points
> To make the algorithm more robust, you can also randomise the feature choice at each node. If n features are available, pick a random subset of $k < n$ features for the algorithm to choose, such as $k = \sqrt{n}$.
3. repeat Steps 1&2 according to the number of trees you prefer (usually > 500 tress)
4. predicted value = average of predicted values across all trees