---
{"dg-publish":true,"permalink":"/notes/k-nearest-neighbor/"}
---


# How it works
1. Choose the number K of neighbours
2. Take the K nearest neighbour of the new data point, according to the Euclidean distance
3. Among these K neighbours, count the number of data points in each category
4. Assign the new data points to the category where you counted the most neighbours
5. Repeat until your model is ready

> If k is selected to be too large, underfitting occurs: the model becomes too generalized and fails to accurately predict the data points in both train and test sets.