---
{"dg-publish":true,"permalink":"/Notes/Database vs Data Warehouse vs Data Lake/","noteIcon":""}
---

# Database vs. Data Warehouse

| [[Notes/Database\|Database]] | [[Notes/Data warehouse\|Data warehouse]] | 
| -- | -- |
| designed for transactions | designed for analytics & reporting |
| fresh & detailed | refreshed periodically and is summarised |
| slow for querying large data | generally faster (do not interfere with any process)|

>[!Important] The process from database to data warehouse is [[Notes/ETL\|ETL]].

## How about Data Lake?
[[Data Lake\|Data Lake]] is a lake for raw data you can throw everything with all formats into it. 