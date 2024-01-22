---
{"topic":"DataScience","dg-publish":true,"permalink":"/Notes/Data Warehouse & Data Lake/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Quote] Designing Machine Learning Systems
>- A repository for storing structured data is called a data warehouse. 
>- A repository for storing unstructured data is called a data lake.

# What is Data Warehouse
- Data Warehouse is a specific type of [[Notes/Database\|Database]] that consolidates data from multiple source systems for data consistency, accuracy, and efficient access.
- The data in the data warehouse is organized into tables, similar to a [[Notes/Database\|Database]], but the tables are optimized for querying and analysis using a schema, with features such as star schemas, fact tables, and dimension tables.

## Database vs. Data Warehouse

| [[Notes/Database\|Database]] | [[Notes/Data warehouse\|Data warehouse]] | 
| -- | -- |
| designed for transactions | designed for analytics & reporting |
| fresh & detailed | refreshed periodically and is summarised |
| slow for querying large data | generally faster (do not interfere with any process)|

>[!Important] The process from database to data warehouse is [[Notes/ETL\|ETL]].

# What is Data Lake
Data lake is a centralized database system that stores large amounts of **raw** data in its original format until it’s needed.
- It is a lake for raw data you can throw everything with all formats into it. 
- It is often used in business intelligence.
## Data Warehouse vs. Data Lake
| **Data warehouse** | **Data lake** |
| --- | --- |
|Data has already been processed and stored in a relational system | Data is raw and unprocessed until it is needed for analysis; additionally, it can have a copy of the entire OLTP or relational database |
|The data’s purpose has already been assigned, and the data is currently in use|The data’s purpose has not been determined yet|
|Making changes to the system can be complicated and require a lot of work|Systems are highly accessible and easy to update|

# What is Data mart
- Data mart is a subject-oriented database that can be a subset of a larger data warehouse, which only focuses on one subject or functional area. 
- Because data marts are generally a copy of data already contained in a data warehouse, they are often fast and simple to implement.

