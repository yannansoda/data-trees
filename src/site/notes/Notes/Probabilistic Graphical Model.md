---
{"topic":"Math","dg-publish":true,"permalink":"/Notes/Probabilistic Graphical Model/","dgPassFrontmatter":true,"noteIcon":""}
---

# Probabilistic Graphical Model 
= a joint probability distribution that uses a **graph structure** to encode conditional independence assumptions. 
## Graph structure
A *Graph* (or Network) is a set of entities (called *Nodes* or Vertices) connected through *Edges*.
- A node has N *degree* of the node = N outgoing and incoming edges
- Two nodes directly connected by an edge are said to be *Adjacent*
- *Parent* = the node at the “entrance” to the edge, *Child* = the one at the “exit” of the edge 
- *path* = sequences of nodes connected by edges

# Directed Acyclic Graph (DAG)
= a special kind of [[Notes/Probabilistic Graphical Model#Graph structure\|Probabilistic Graphical Model#Graph structure]] with:
1. directed edges (every edge has a direction: from parent → child)
2. no cycles — you can’t start at a node and follow a path that loops back to it

### Bayesian Network
= a type of DAG that represents probabilistic relationships between variables (although there is nothing inherently Bayesian about such models)
- each node is a random variable
- each edge is a directed connection indicating a probabilistic dependency (not just correlation or causation, but conditional probability)
- each node is conditionally independent of all its predecessors given its parents, i.e. showing Markov property ([[Notes/Markov Chain#^b013c4\|Markov Chain#^b013c4]])