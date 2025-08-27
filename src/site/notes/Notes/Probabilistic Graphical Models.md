---
{"topic":"Statistics, Modeling","dg-publish":true,"permalink":"/Notes/Probabilistic Graphical Models/","dgPassFrontmatter":true,"noteIcon":""}
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
= a special kind of [[Notes/Probabilistic Graphical Models#Graph structure\|Probabilistic Graphical Models#Graph structure]] with:
1. directed edges (every edge has a direction: from parent → child)
2. no cycles — you can’t start at a node and follow a path that loops back to it
## Bayesian Network
= a type of DAG that represents probabilistic relationships between variables (although there is nothing inherently Bayesian about such models)
- each node is a random variable
- each edge is a directed connection indicating a probabilistic dependency (not just correlation or causation, but conditional probability)
- each node is conditionally independent of all its predecessors given its parents, i.e. showing Markov property ([[Notes/Markov Chain#^b013c4\|Markov Chain#^b013c4]])

## Basic Causal Structures
- create or remove associations between variables
- key to deciding **when to adjust** for a variable and when **not** to adjust

| Confound type    | DAG structure (schematic)                         | Description                                                                                                                                     | Adjustment implications / Take care...                                                                                     | Example                                                                                                               |
| ---------------- | ------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **The Fork**     | X ← Z → Y                                         | Z is a **common cause** of X and Y. This creates a spurious association between X and Y if not controlled.                                      | Must adjust for Z to block confounding.                                                                                    | Age (Z) affects both exercise (X) and health outcomes (Y).                                                            |
| **The Pipe**     | X → Z → Y                                         | Z is a **mediator** (on the causal pathway from X to Y).                                                                                        | Adjusting for Z blocks part of the causal effect → **post-treatment bias**. Don’t condition if interested in total effect. | Smoking (X) → blood pressure (Z) → heart disease (Y).                                                                 |
| **The Collider** | X → Z ← Y                                         | Z is a **collider** (caused by both X and Y). By default, X and Y are independent. Conditioning on Z opens a spurious path → **collider bias**. | Do **not** adjust for Z.                                                                                                   | Genetics (X) and environment (Y) both affect admission to college (Z). Conditioning on Z creates a false association. |

## Identification Strategies

### Back-Door Criterion
= A graphical method for identifying a set of variables to adjust for, in order to estimate the causal effect of X on Y
- **Idea**: Block all “back-door paths” (paths that go into X through an arrow pointing backward) between treatment and outcome.  
- **Formal definition**: A set of variables Z satisfies the back-door criterion relative to (X, Y) if:
  1. No node in Z is a descendant of X  
  2. Z blocks every path between X and Y that has an arrow into X  

- **Adjustment formula**:  
$$
P(Y \mid do(X)) = \sum_{z} P(Y \mid X, Z=z) P(Z=z)
$$

- **Intuition**: Control for confounders that create spurious associations.  
- **Example**: Age is a confounder of Exercise (X) and Health (Y). Adjusting for Age satisfies the back-door criterion.
### Front-Door Criterion
= A graphical method that can identify causal effects **even with unmeasured confounders**, if there exists a mediator we can observe.  
- **Idea**: Use a mediator M that transmits the effect of X on Y.  
- **Conditions** (Pearl):
  1. M intercepts all directed paths from X to Y  
  2. There are no unblocked back-door paths from X to M  
  3. All back-door paths from M to Y are blocked by X  

- **Adjustment formula**:  
$$
P(Y \mid do(X)) = \sum_m P(M \mid X) \sum_{x'} P(Y \mid M, X=x') P(X=x')
$$

- **Intuition**: Even if X and Y are confounded, we can identify the causal effect through the mediator M.  
- **Example**: X = smoking, M = tar deposits in lungs, Y = lung cancer.  
  - There may be unmeasured confounders (e.g., genetic risk) affecting smoking and lung cancer, but tar (M) perfectly mediates the causal pathway.
