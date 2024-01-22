---
{"topic":"DataScience","dg-publish":true,"permalink":"/Notes/Data Engineering Fundamentals/","dgPassFrontmatter":true,"noteIcon":""}
---

# Data serialization
= The process of converting a data structure or object state into a format that can be stored or transmitted and reconstructed later.
### Types of data serialization formats

| Format   | Binary/Text    | Human-readable | Example use cases             | Features |
| -------- | -------------- | -------------- | ----------------------------- | --------|
| JSON     | Text           | Yes            | Everywhere                    |         |
| CSV      | Text           | Yes            | Everywhere                    | row-major |
| Parquet  | Binary         | No             | Hadoop, Amazon Redshift       | column-major |
| Avro     | Binary primary | No             | Hadoop                        |     |
| Protobuf | Binary primary | No             | Google, TensorFlow (TFRecord) |     |
| Pickle   | Binary         | No             | Python, PyTorch serialization |    |


# Data models
[[Notes/Database\|Database]]

# Data Storage Engines and Processing
- [[Notes/Database#Transactional & Analytical Processing\|Database#Transactional & Analytical Processing]]
- [[Notes/ETL\|ETL]]