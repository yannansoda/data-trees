---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/Notes/Machine Learning Systems Design/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Note]
>Most of the notes are from the book Machine Learning Systems Design
# Overview of Machine Learning Systems Design
![Pasted image 20230622120707.png|500](/img/user/assets/images/Pasted%20image%2020230622120707.png)

# MLOps
MLOps = Machine Learning Operations
- Ops in MLOps comes from DevOps, short for Developments and Operations. 
- To operationalize something means to bring it into production, which includes deploying, monitoring, and maintaining it. 
- MLOps is a set of tools and best practices for bringing ML into production.


ML in research vs. ML in production
These are important for ML in production than in research:
- stakeholder involvement
- computational priority
- the properties of data used
- the gravity of fairness issues
-  the requirements for interpretability

# Requirements for ML Systems
### Reliability
### Scalability
- resource scaling
- artifact management
### Maintainability
### Adaptability 
- data distribution shifts
- [[Continual Learning\|Continual Learning]]

# Iterative Process of Developing an ML system
1. Project scoping
2. Data engineering
3. ML model development
4. [[Notes/ML Model Deployment\|ML Model Deployment]]
5. [[Notes/ML System Monitoring and Continual learning\|ML System Monitoring and Continual learning]]
6. Business analysis

# Infrastructure and Tooling for MLOps
### Infrastructure 
![Pasted image 20230714122416.png|400](/img/user/assets/images/Pasted%20image%2020230714122416.png)
### Storage & Compute
- storage layer: where data is collected and stored
	- hard drive disk (HDD), solid state disk (SSD)
	- [[Notes/AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)\|AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)]], Snowflake
- compute layer: all the compute resources a company has access to and the mechanism to determine how these resources can be used
	- CPU, GPU
	- [[Notes/Amazon EC2\|Amazon EC2]], GCP
### Development Environment
- IDE (Integrated development environment)
	- cloud IDE: AWS Cloud9, Amaon SageMaker Studio
- versioning
- CI/CD
### Resource Management
- Cron, Schedulers, Orchestrators
	- cron: it run a script at a predetermined time and tell you whether the job succeeds or fails
	- scheduler & orchestrator
		- scheduler: cron programs deciding when 
		- orchestrator: cron programs concerning where to get resources. e.g. Kubernetes
		- scheduler and orchestrator can be used interchangeably 
- Data science workflow management ![Pasted image 20230719161709.png|400](/img/user/assets/images/Pasted%20image%2020230719161709.png)
### Pipeline Orchestration
orchestration allows managing end to end traceability of pipeline using automation to capture specific inputs, outputs, and artifacts of a given task. 
- Model lineage
	- for each version of a trained model, versions of
		- data used
		- code/hyperparamters used
		- algorithm/framework
		- training docker image
		- packages/libraries 
- Model registry
{ #8e6855}

	- centrally manage model metadata and model artifacts
	- track which models are deployed across environments
- Artifact tracking
	- artifact = the output of a step or task can be consumed by the next step in a pipeline or deployed directly for consumption
# Coping with ML training challenges
### Checkpointing
- check points include
	- model architecture
	- model weights
	- training configurations
	- optimizer
- take two things into consideration: frequency and number of checkpoints
### Distributed training strategies 
-> scale challenges: increased training data volume or increased model size and complexity
- Distributed training = split training load across multiple compute nodes or clusters (CPU/GPU)
- there are two strategies
	- data parallelism: training data split up + model replicated on all notes
	- model parallelism: training data replicated + model split up on all nodes
	- which to choose: ![Pasted image 20231004115356.png|400](/img/user/assets/images/Pasted%20image%2020231004115356.png)

# Model Integration
= integrating models with ML applications


# Human-in-the-Loop Pipelines
### Human review of model predictions 
![Pasted image 20231004110235.png|500](/img/user/assets/images/Pasted%20image%2020231004110235.png)