---
{"topic":"DataScience, DeepLearning","dg-publish":true,"permalink":"/StudyNotes/Graph Neural Networks/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Source]
>- [Graph Neural Networks Part 1. Graph Convolutional Networks Explained](/https:/towardsdatascience.com/graph-neural-networks-part-1-graph-convolutional-networks-explained-9c6aaa8a406e)
>- [Graph Neural Networks Part 2. Graph Attention Networks vs. Graph Convolutional Networks](https://towardsdatascience.com/graph-neural-networks-part-2-graph-attention-networks-vs-gcns-029efd7a1d92)
## What is GNN
- A GNN is a type of neural network specifically designed to process and analyze data structured as graphs.
>[!What is Graph]
> - A graph is represented as:
> 	- Nodes (vertices): Represent entities or objects.
> 	- Edges: Represent relationships between nodes. Edges can be directed or undirected, weighted or unweighted.
> 	- Features: Both nodes and edges can have associated feature vectors. For example, in a social network graph, a node may have features like user age, and an edge could represent friendship with a weight indicating connection strength.
>- Graphs are  useful for representing complex relationships like social networks, molecular structures, or transportation systems. Traditional neural networks, which are designed for grid-like data (e.g., images, sequences), cannot directly handle such irregular structures.

- common types of prediction tasks in graphs
	- **on graph level**: classify the entire graph (e.g., classifying a molecular graph)
	- **on node level**: classify nodes (e.g., predict a property of a user in a social network)
	- **on edge level**: predict the value of an edge (e.g. recommended friends on social media)

## How GNN works
GNN learns a representation for each node by aggregating information from its neighbors.
1. **Message Passing:** Each node gathers information from its neighbors
2. **Aggregation**: The messages from neighboring nodes are combined (summed, averaged, or through more complex operations)
3. **Update**: The node’s feature is updated using the aggregated message, often by applying a neural network

## Common GNN Variants
### Graph Convolutional Networks (GCNs)
- extends the idea of convolution to graphs by computing weighted averages of neighboring nodes' features.

### Graph Attention Networks (GATs)
- uses attention mechanisms to assign different weights to neighboring nodes during the aggregation step
### GraphSAGE
- instead of aggregating all neighbors, GraphSAGE samples a fixed-size set of neighbors for more scalable training.