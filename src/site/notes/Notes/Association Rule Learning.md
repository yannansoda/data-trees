---
{"dg-publish":true,"permalink":"/Notes/Association Rule Learning/","noteIcon":""}
---

# Apriori
## How it works
> The association scenario can be movie or product recommendations: "People watched/bought A also watched/bought what.... B or C or something else? 

$$
support (M) = \frac{\#\ user\ watchlists\ containing\ M}{\#\ user\ watchlists}
$$
$$
confidence (M_1 -> M_2) = \frac{\#\ user\ watchlists\ containing\ M_1\ and\ M_2}{\#\ user\ watchlists\ containing\ M_1}
$$

$$
lift (M_1 -> M_2) = \frac{confidence(M_1 -> M_2)}{support(M_1)}
$$
1. set a minimum support and confidence
2. take all the subsets in transactions having higher support than minimum support
3. take all the association rules of these subjects having higher confidence than minimum confidence
4. sort the rules by decreasing lift

>  `sklearn` does not include Apriori modules!!! Use `apyori` instead.

# Eclat
Eclat is similar to Apriori but only uses support
## How it works
1. set a minimum support
2. take all the subsets in transactions having higher support than minimum support
3. sort these subsets by decreasing support