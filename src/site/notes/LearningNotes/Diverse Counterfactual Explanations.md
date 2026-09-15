---
{"topic":"MachineLearning, ExplainableAI","dg-publish":true,"permalink":"/LearningNotes/Diverse Counterfactual Explanations/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"MachineLearning, ExplainableAI"}}
---

> [!Summary] 
> DiCE generates **multiple different ways** to change an input so that a model gives a desired prediction.
> It belongs to [[LearningNotes/Interpretable Machine Learning#Counterfactual explanations\|Interpretable Machine Learning#Counterfactual explanations]], and  [[LearningNotes/Evolutionary Algorithms\|Evolutionary Algorithms]] can be used as one search engine inside DiCE.

# Definition
Diverse Counterfactual Explanations (DiCE) is a method for generating counterfactual explanations for machine learning predictions.

A counterfactual explanation asks:

> What small change to this input would change the model prediction?

DiCE extends this idea by asking:

> What are several different small changes that could change the model prediction?


# Why "diverse" - why diversity matters
One counterfactual can be technically correct but practically unhelpful.

DiCE tries to generate a set of counterfactuals that are:
- **valid**: they change the prediction to the desired class
- **close**: they do not change too many features too much
- **diverse**: they offer meaningfully different alternatives
- **actionable**: they avoid impossible or forbidden changes when constraints are given

# How it works
1. Take an original input $x$ and its current prediction.
2. Define a desired prediction.
3. Generate candidate counterfactuals $x'$.
4. Score each candidate by several criteria:
	- does it produce the desired prediction?
	- how far is it from the original input?
	- how different is it from other counterfactuals?
	- does it satisfy constraints?
5. Search for a set of counterfactuals that balances these criteria.

## Objective
DiCE is usually balancing three goals:
### Validity
The counterfactual should flip the prediction.
Example:
- original prediction: reject loan
- counterfactual prediction: approve loan
### Proximity
The counterfactual should be close to the original input.
Example:
- changing income from 50k to 55k is more reasonable than changing it from 50k to 500k
### Diversity
The counterfactuals should not all say the same thing.
Example:
- bad diversity:
	- income +10k
	- income +11k
	- income +12k
- better diversity:
	- income +10k
	- loan amount -5k
	- debt ratio -10%

# Search engines for DiCE
DiCE is the explanation method, but it still needs a **search engine** to find good counterfactuals.

The search engine is the procedure that tries many possible $x'$ values and looks for candidates that are valid, close, diverse, and realistic.

> [!Important]
> The search engine affects what kinds of counterfactuals are found. DiCE's explanation quality depends not only on the idea of diversity, but also on whether the search procedure can find realistic and actionable candidates.

## Search Engines

| Search Engine                         | How it works                                                                                                                         | When to use                                                                                                                                                                                                                                                                                |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Random search**                     | generates many random changes around the original input<br>keeps the candidates that work                                            | - use as a simple baseline<br>- when the feature space is small<br>- when the model is black-box<br>- when gradients are unavailable<br>- less useful when valid counterfactuals are rare                                                                                                  |
| **Genetic algorithm**                 | keeps a population of candidate counterfactuals and gradually improves them using [[LearningNotes/Evolutionary Algorithms#Genetic Algorithm (GA)\|Evolutionary Algorithms#Genetic Algorithm (GA)]] | - when the model is black-box<br>- when the search space is mixed: continuous + categorical + integer features<br>- when the objective is non-smooth or constrained<br>- when random search is too inefficient<br>- can be slower because it needs many model evaluations                  |
| **Gradient-based search**             | directly optimizes the counterfactual input using gradients                                                                          | - useful for differentiable models, especially neural networks<br>- when features are mostly continuous<br>- usually faster than random or genetic search<br>- less suitable for tree models, categorical-heavy data, or hard constraints                                                  |
| **Nearest-neighbor / KD-tree search** | looks for real examples in the dataset that already have the desired outcome                                                         | - when realism is important<br>- when you want counterfactuals close to actual observed data<br>- useful for tabular data<br>- less useful if the dataset has few examples with the desired outcome<br>- useful in very high-dimensional spaces where nearest-neighbor search becomes weak |


## Choosing a search engine
| Situation                                         | Better engine                                               |
| ------------------------------------------------- | ----------------------------------------------------------- |
| Need a simple baseline                            | Random search                                               |
| Black-box model                                   | Random search or genetic search                             |
| Many categorical / integer features               | Genetic search                                              |
| Mostly continuous features + differentiable model | Gradient-based search                                       |
| Need realistic examples close to observed data    | Nearest-neighbor / KD-tree search                           |
| Valid counterfactuals are rare                    | Genetic search or gradient-based search                     |
| Need fast approximate results                     | Gradient-based search if available; otherwise random search |



# Comparison with other local explanations
| Method                     | Main question                                             |
| -------------------------- | --------------------------------------------------------- |
| LIME                       | What simple local model explains this prediction?         |
| SHAP                       | How much did each feature contribute to this prediction?  |
| Counterfactual explanation | What minimal change would flip this prediction?           |
| DiCE                       | What are multiple different ways to flip this prediction? |

# Pros & Cons
## Pros
- gives actionable “what-if” explanations
- provides multiple options instead of one answer
- can work with black-box models
- useful for individual-level decision explanation
- can include constraints on which features are changeable

## Cons
- counterfactuals may still be unrealistic if constraints are poorly defined
- sensitive to distance metrics and feature scaling
- generating diverse counterfactuals can be computationally expensive
- does not automatically solve fairness or causality problems
- multiple valid counterfactuals may conflict with domain knowledge

# Important caveats
- Counterfactual explanations are not automatically causal.
- A feature change that flips the model prediction does not necessarily mean that changing it in the real world will cause the outcome to change.
- Actionability constraints are important.
- Immutable features should usually not be changed.


>[!info] Related Notes
>- [[LearningNotes/Interpretable Machine Learning\|Interpretable Machine Learning]]
>- [[LearningNotes/Evolutionary Algorithms\|Evolutionary Algorithms]]
>- [[LearningNotes/Optimization Algorithms\|Optimization Algorithms]]
>- [[LearningNotes/Hyperparameter Tuning\|Hyperparameter Tuning]]