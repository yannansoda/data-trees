---
{"topic":"DataScience, CloudComputing","dg-publish":true,"permalink":"/Notes/AWS for Data Science/","dgPassFrontmatter":true,"noteIcon":""}
---


![Pasted image 20230706105550.png](/img/user/assets/images/Pasted%20image%2020230706105550.png)

# Data Sources
- **Amazon S3** ([[Notes/AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)\|AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)]])

# Data Storage
- **Amazon RDS**: transactional data ([[Notes/AWS Storage & Databases#Amazon Relational Database Service (Amazon RDS)\|AWS Storage & Databases#Amazon Relational Database Service (Amazon RDS)]])
- **Amazon S3**: file-based data ([[Notes/AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)\|AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)]])
- **Amazon Redshift**: analytical data ([[Notes/AWS Storage & Databases#Amazon Redshift\|AWS Storage & Databases#Amazon Redshift]])
- **Amazon DynamoDB**: non-relational data ([[Notes/AWS Storage & Databases#Amazon DynamoDB\|AWS Storage & Databases#Amazon DynamoDB]])
# Data Ingestion & Processing
![Pasted image 20230706173206.png](/img/user/assets/images/Pasted%20image%2020230706173206.png)
- Batch processing: Processes massive amounts of data at once
	- **AWS Lambda** ([[Notes/AWS All-in-one#^08bc66\|AWS All-in-one#^08bc66]])
	- **AWS Glue Data Catalog**
		- = ETL service for data management
		- register data: create reference to data
		- only stores metadata/schema in the catalog, no data is moved
	- **Amazon EMR**
		- Hadoop and Spark as a service, running at any scale with no complex setup.
- Stream processing: Processes tiny bursts of data continuously
	- **Amazon Kinesis**
		- Amazon Kinesis Data Firehose: 
			- capture, transform, and load data streams into AWS data stores for near real-time analytics with existing business intelligence tools. 
		- Amazon Kinesis Data Streams:
			- build custom, real-time applications that process data streams using popular stream processing frameworks. 
		- Amazon Kinesis Video Streams: 
			- stream video from connected devices to AWS
		- Amazon Kinesis Data Analytics:
			- process data streams in real time with SQL or Java without having to learn new programming languages or processing frameworks.

# Data Lake
- **Amazon S3** ([[Notes/AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)\|AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)]]) 

# Data Warehouse
- **Amazon Redshift** ([[Notes/AWS Storage & Databases#Amazon Redshift\|AWS Storage & Databases#Amazon Redshift]])

# Data Consuming/Visualization 
- **Amazon Athena**
	- query data in S3 using SQL
- **Amazon QuickSight**
	-  cloud-powered business intelligence (BI) service for data visualization 
- **Amazon Elasticsearch**
	- operational analytics
- **Amazon Redshift** 

# ML Modeling
>[!Quote] Machine learning workflow
>![Pasted image 20231003113126.png|600](/img/user/assets/images/Pasted%20image%2020231003113126.png)
- [[Notes/Amazon SageMaker\|Amazon SageMaker]]
- **Amazon Augmented AI (Amazon A2I)**
	- for [[Notes/Machine Learning Systems Design#Human review of model predictions\|Machine Learning Systems Design#Human review of model predictions]]
	- steps
		- define human workforce -> define task UI -> define human review workflow
			- -> start human loop with AWS AI Service API calls
			- -> start human loop with custom ML models



