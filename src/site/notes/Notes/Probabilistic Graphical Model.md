---
{"topic":"Math","dg-publish":true,"permalink":"/Notes/Probabilistic Graphical Model/","dgPassFrontmatter":true,"noteIcon":""}
---

Probabilistic Graphical Model = a joint probability distribution that uses a graph structure to encode conditional independence assumptions. 

### Directed acyclic graph
When the graph is a directed acyclic graph or DAG like this:

 ![Pasted image 20231001121109.png|100](/img/user/_assets/images/Pasted%20image%2020231001121109.png)
 
the model is sometimes called a Bayesian network, although there is nothing inherently Bayesian about such models.
In the Directed acyclic graph case, each node is conditionally independent of all its predecessors given its parents, i.e. showing Markov property ([[Notes/Markov Chain#^b013c4\|Markov Chain#^b013c4]])