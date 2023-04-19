### Summary of Athena
Analyze petabyte-scale data on [[S3]] with ease and flexibility - no need for ETL. Build interactive, advanced analytics applications using data on premises, in your data lake, or in cloud stores serverless. #AWSService 

### Athena Details
- Serverless with automatic scaling and configuration. No indexes.
- Define DDL statements or use [[Glue]] out-of-the-box to automatically crawl data sources and populate Data Catalog.
- Athena uses [[Presto]] a distributed SQL query engine so ANSI SQL can be used against large data sets in S3.
- Data formats CSV, [[JSON]], [[ORC]], [[Avro]], or [[Parquet]].
- Run queries from Athena console, API, CLI, SDK, JDBC and ODBC.
 
**Federated query**
Connectors for enterprise data sources including [[DynamoDB]], [[Redshift]], [[OpenSearch]], MySQL, PostgreSQL, Redis. Often used with QuickSight.
![[lambda-source-connector-solution.png|256]]
Fig. Federated query via Lambda as connector

- Invoke ML models from [[SageMaker]] within SQL queries for anomaly detection, customer cohort analysis and sales predictions.

#UseCase Query VPC flow logs, ELB logs, CloudTrail logs. Good for ad-hoc queries - for warehouse level aggregations use [[Redshift]]

![[athena-s3-quicksight-solution.png|96]]
Fig. Architecture


* Analyze petabyte-scale data where it lives with ease and flexibility.
* S3 SQL. Pre-configured to work with Glue.
* Query service to analyze data using SQL. It is serverless.
* Use cases: run federated queries across relational, nonrelational, object, and custom data sources running on premises or in the cloud. Use ML models in SQL queries or Python. Build distributed big data reconciliation engines. Analyze google analytics data by using AppFlow to store in S3 to query it.
#### Performance and Cost Optimization
> Pay per query based on amount of data scanned. Save by compressing data, partitioning buckets by column, or converting data to columnar format like Parquet. Use larger files > 128 MB than many smaller files. #performant  #CostOptimized #BestPractice 

![[CostSavingsAthena.png|512]]
Fig Performance and Cost Optimization

#### References for Athena
1. https://aws.amazon.com/athena/features/
2. [Athena](https://aws.amazon.com/athena/) 

---
Created on 2023-03-14 13:57