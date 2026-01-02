---
{"topic":"DataScience, CloudComputing","dg-publish":true,"permalink":"/StudyNotes/AWS Storage & Databases/","dgPassFrontmatter":true,"noteIcon":""}
---


| storage service                                                             | features                                                                                             |
| --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| [[StudyNotes/AWS Storage & Databases#Amazon Elastic Block Store (Amazon EBS)\|AWS Storage & Databases#Amazon Elastic Block Store (Amazon EBS)]]         | Block-level storage for EC2 instances that persists data even after termination                      |
| [[StudyNotes/AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)\|AWS Storage & Databases#Amazon Simple Storage Service (Amazon S3)]]       | Object-level storage that can be accessed from anywhere on the web                                   |
| [[StudyNotes/AWS Storage & Databases#Amazon Elastic File System (Amazon EFS)\|AWS Storage & Databases#Amazon Elastic File System (Amazon EFS)]]         | Fully managed file storage for EC2 instances that allows simultaneous access from multiple instances |
| [[StudyNotes/AWS Storage & Databases#Amazon Relational Database Service (Amazon RDS)\|AWS Storage & Databases#Amazon Relational Database Service (Amazon RDS)]] | -                                                                                                    |
|                                                                             |                                                                                                      |
>[!important]
>**Object storage vs. Block storage**
>- Object storage treats any file as a complete, discreet object. 
>- Block storage breaks files down to small component parts or blocks for complex reading, writing, changing functions.

### Amazon Elastic Block Store (Amazon EBS) 
Because an instance store provides only **temporary** block-level storage for an Amazon EC2 instance, we need storage services that can **persist data after EC2 termination**.
- block-level storage for EC2 instances that persists data even after termination
- need to define configuration
- need to take incremental backups using Amazon EBS snapshots 
	- incremental = only the data that have changed since the most recent snapshot is backed up ![Pasted image 20230629110728.png|400](/img/user/_assets/images/Pasted%20image%2020230629110728.png)
### Amazon Simple Storage Service (Amazon S3)
- object-level storage that stores data as objects in buckets
- data can be accessed with an object key along with the bucket name
- unlimited storage space, with the maximum file size for an object as 5 TB
- web enabled
- perfect foundation for Data Lake ([[StudyNotes/Data Warehouse & Data Lake\|Data Warehouse & Data Lake]])
- can choose from a range of storage classes:

 | Amazon S3 class                                       | features                                                                                         | costs                                                                                  |
 | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------- |
 | Amazon S3 Standard                                    | for frequently accessed data; stores data in >= three Availability Zones                         | -                                                                                      |
 | Amazon S3 Standard-Infrequent Access (S3 Standard-IA) | for infrequently accessed data                                                                   | similar to Amazon S3 Standard but has a lower storage price and higher retrieval price |
 | Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA) | stores data in a single availability zone                                                        | lower storage price than Amazon S3 Standard-IA                                         |
 | Amazon S3 Intelligent-Tiering                         | for data with unknown or changing access patterns                                                | a small monthly monitoring and automation fee per object                               |
 | Amazon S3 Glacier Instant Retrieval                   | for archived data that requires immediate access; can retrieve objects within a few milliseconds | -                                                                                      |
 | Amazon S3 Glacier Flexible Retrieval                  | for archived data; can retrieve objects within a few minutes to hours                            | low-cost storage class for data archiving                                              |
 | Amazon S3 Glacier Deep Archive                        | for archived data; can retrieve objects within 12 hours                                          | lowest-cost object storage class ideal for archiving                                   |
 | Amazon S3 Outposts                                    | creates S3 buckets on Amazon S3 Outposts for retrieving, storing, accessing                      | - |                                                                          |                                                                                        |

### Amazon Elastic File System (Amazon EFS)
- a scalable file system used with AWS Cloud services and on-premises resources
- regional resource
- Linux file system

>![Important] Amazon EBS vs. EFS
>
>| EBS | EFS |
>| -- | -- |
>| stores data in a **single** [[StudyNotes/AWS Global infrastructure & Networking#Availability zone\|AWS Global infrastructure & Networking#Availability zone]] | stores data in **multiple** [[StudyNotes/AWS Global infrastructure & Networking#Availability zone\|AWS Global infrastructure & Networking#Availability zone]] |

### Amazon Relational Database Service (Amazon RDS)
- enables to run relational databases in the AWS Cloud
- provides services: automated patching, backups, redundancy, failover, disaster recovery
- Amazon RDS database engines
	- Amazon Aurora
		- an enterprise-class relational database
		- compatible with MySQL and PostgreSQL
		- faster than standard MySQL and PostgreSQL databases
	- PostgreSQL
	- MySQL
	- MariaDB
	- Oracle Database
	- Microsoft SQL Server
### Amazon DynamoDB
- key-value and document non-relational database (NoSQL)
- features
	- Serverless
		- you do not have to provision, patch, or manage severs
		- you do not have to install, maintain, or operate software
	- Automatic scaling: [[StudyNotes/AWS All-in-one#^c7080d\|AWS All-in-one#^c7080d]]
	- highly scalable
	- ms 
### Amazon Neptune 
- graph database service
### Amazon Redshift
- a data warehousing service for big data analytics
- offers the ability to collect data from many sources
### AWS Database Migration Service
- enables migrating relational databases, nonrelational databases, and other types of data stores
- move data between a source database and a target database
### Additional database services
| service                                      | usage                                                                                    |
| -------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Amazon DocumentDB                            | document database service                                                                |
| Amazon Neptune                               | graph database service                                                                   |
| Amazon Quantum Ledger Database (Amazon QLDB) | ledger database service                                                                  |
| Amazon Managed Blockchain                    | create and manage blockchain networks with open-source frameworks                        |
| Amazon ElastiCache                           | add caching layers on top of databases to help improve the read times of common requests |
|Amazon DynamoDB Accelerator (DAX) |      in-memory cache for DynamoDB  |