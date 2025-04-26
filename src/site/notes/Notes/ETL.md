---
{"topic":"DataEngineering","dg-publish":true,"permalink":"/Notes/ETL/","dgPassFrontmatter":true,"noteIcon":""}
---

- ETL = Extract, Transform, Load 
- ETL is a type of data pipeline that enables data to be gathered from source systems, converted into a useful format, and brought into a data warehouse or other unified destination system. 
 >[!Idea] Data pipeline = a series of processes that transports data from different sources to their final destination for storage and analysis



![Pasted image 20230305105317.png|500](/img/user/_assets/images/Pasted%20image%2020230305105317.png)

## ETL quality
- what ETL quality testing should be taking into account:
	- Completeness: Does the data contain all of the desired components or measures?
	- Consistency: Is the data compatible and in agreement across all systems?
	- Conformity: Does the data fit the required destination format?
	- Accuracy: Does the data conform to the actual entity being measured or described?
	- Redundancy: Is only the necessary data being moved, transformed, and stored for use
	- Timeliness: Is the data current?
	- Integrity: Is the data accurate, complete, consistent, and trustworthy? (Integrity is influenced by the previously mentioned qualities.)
- parts of these qualities are also covered in [[Notes/Data Veracity\|Data Veracity]] and [[Notes/Big Data#The V's of big data\|Big Data#The V's of big data]]
# ETL vs. ELT
>[!New] ELT = Extract, Transform, Load

|**Differences**|**ETL**|**ELT**|
|---|---|---|
|The order of extraction, transformation, and loading data|Data is extracted, transformed in a staging area, and loaded into the target system|Data is extracted, loaded into the target system, and transformed as needed for analysis|
|Location of transformations|Data is moved to a staging area where it is transformed before delivery|Data is transformed in the destination system, so no staging area is required|



