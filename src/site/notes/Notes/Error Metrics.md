---
{"dg-publish":true,"permalink":"/Notes/Error Metrics/","noteIcon":""}
---


## Regression Metrics:
- Mean Absolute Error (MAE)
	- measures the absolute difference between the predicted and actual values.
	- Be careful about MAE. Compared to MSE, it does not penalize large errors. But if your loss ([[Notes/Cost Functions\|Cost Functions]]) is just proportional to the size of error, then maybe MAE is better.
- Mean Squared Error (MSE)
	- measures the squared difference between the predicted and actual values.
- Root Mean Squared Error (RMSE)
	- the square root of the MSE, which provides a measure of the average magnitude of the error.
- R-squared (R^2): measures the proportion of variance in the target variable that is explained by the model.

### Classification Metrics:
>[!Source]
>See [[Notes/Confusion Matrix#Performance measures\|Confusion Matrix#Performance measures]]
- Accuracy
	- measures the proportion of correct predictions out of total predictions.
- Precision
	- measures the proportion of true positives (correctly predicted positives) out of all predicted positives.
- Recall (Sensitivity) 
	- measures the proportion of true positives out of all actual positives.
- F1 score
	- a weighted average of precision and recall that balances both measures.
- ROC curve
	- [[Notes/Confusion Matrix#Receiver Operating Characteristic (ROC)\|Confusion Matrix#Receiver Operating Characteristic (ROC)]]
	- ROC characteristics: only works for binary classification
	- ROC AUC: area under ROC curve, works for multiclass

### Time Series Metrics
- MAE
- MSE
- Mean Absolute Percentage Error (MAPE): measures the percentage difference between the predicted and actual values.
- Symmetric Mean Absolute Percentage Error (SMAPE): similar to MAPE, but takes the average of the percentage difference between the predicted and actual values and the percentage difference between the actual and predicted values.
- Mean Absolute Scaled Error (MASE): measures the relative accuracy of forecasts compared to a naive forecast based on the historical data.
