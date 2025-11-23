---
{"topic":"DataScience, MachineLearning, CloudComputing","dg-publish":true,"permalink":"/Notes/Amazon SageMaker/","dgPassFrontmatter":true,"noteIcon":""}
---


# Train a custom model with Amazon SageMaker
1. configure dataset (Amazon S3 URL, computing instance, or path for storing the training code in Amazon Elastic Container Registry (ECR)) & evaluation metrics (Amazon CloudWatch Logs)
2. configure hyperparameters
3. provide training script
4. fit the model
# Features
>[!Quote] Machine learning workflow
>![Pasted image 20231003113126.png|600](/img/user/_assets/images/Pasted%20image%2020231003113126.png)
- **SageMaker Data Wrangler**
	- connect pandas DataFrames and AWS data services
	- load and upload data
- **SageMaker Clarify**
- **SageMaker Processing Jobs**
- **SageMaker Feature Store**
	- store and serve features
	- reduce skew
	- real time & batch
- **SageMaker Autopilot**
{ #a5ba5d}

	- cover all steps in [[Notes/AutoML\|AutoML]]: ingest & analyze data -> prepare & transform data -> train & tune model 
	- automatically generate notebooks (candidate generation notebook (provides links to the data preprocessor Python scripts, the algorithms, and the algorithm hyperparameters selected by Autopilot), data exploration notebook) and codes
- **SageMaker Debugger**
	- capture real-time debugging data during model training in Amazon SageMaker
		- system metrics: CPU&GPU utilization, data I/O metrics
		- framework metrics: 
			- convolutional operations in forward pass
			- batch normalization operations in backward pass
			- data loader processes between steps
			- gradient descent algorithm operations
		- output tensors: scalar values (accuracy and loss); matrices (weights, gradients, input & output layers)
	- if bugs, actions can be taken via
		- Amazon CloudWatch Event: send SMS etc
		- Amazon SageMaker Notebook: analyze
		- Amazon SageMaker Studio: visualize
- **SageMaker Hyperparameter Tuning**
	- steps: create an Estimator -> define the combination of hyperparameters -> start a SageMaker hyperparameter tuning job -> analyze results and select the best model candidate
	- a "warm start" feature: reuses results from a previous hyperparameter training job
		- scenarios: 
			- you want to change the hyperparameter tuning ranges from the previous job -> use type "identical data and algorithm"
			- you want to add new hyperparameters -> use type "transfer learning"
- [[Notes/ML Model Deployment\|ML Model Deployment]] with SageMaker ![Pasted image 20231005094917.png|500](/img/user/_assets/images/Pasted%20image%2020231005094917.png)
	- **SageMaker Endpoint**
		- real-time prediction [[Notes/ML Model Deployment#^b2b283\|ML Model Deployment#^b2b283]]
		- auto-scaling
			- pipeline of creating SageMaker production variants with Endpoint: 
				- construct Docker Image URI -> create SageMaker models  -> create production variants -> create endpoint configuration -> create endpoint
	- **SageMaker Batch Transform**
		- batch prediction [[Notes/ML Model Deployment#^50c5c9\|ML Model Deployment#^50c5c9]]
- **SageMaker Pipelines**
	- SageMaker model registry: for [[Notes/Machine Learning Systems Design#^8e6855\|Machine Learning Systems Design#^8e6855]]
- **SageMaker Model Monitor**
- **SageMaker Ground Truth**
	- for [[Notes/Best Practices & Common Pitfalls in Machine Learning#Data Labeling & Label Quality\|Best Practices & Common Pitfalls in Machine Learning#Data Labeling & Label Quality]]
	- job workflow: setup input data -> select labelling task -> select human workforce -> create task UI
	- human workforce options: Amazon Mechanical Turk/Private/vendor
- **SageMaker Projects**
	- integrates automatically with SageMaker Pipelines and SageMaker model registry
	-  create MLOps solutions to orchestrate and manage your end to end machine learning pipelines, while also incorporating CI/CD practices
- SageMaker Managed Spot Training: for [[Notes/Machine Learning Systems Design#Checkpointing\|Machine Learning Systems Design#Checkpointing]]
- Amazon SageMaker BlazingText: unlike [[Notes/Natural Language Processing#^ff7c47\|Natural Language Processing#^ff7c47]], it is a word2vec model