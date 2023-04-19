AWS offers [[Athena]], [[Redshift]], [[OpenSearch]], [[Kinesis#Kinesis Data Stream]], [[Kinesis#Kinesis Data Firehose]],  [[EMR]], [[QuickSight]], [[Glue]], [[Lake Formation]] and [[Flink]].


| Service         | Purpose                      | Architecture                                                   |
| ------------------ | ---------------------------- | -------------------------------------------------------------- |
| [[Redshift]]       | Data warehouse               | Handles exabyte-scale data. Indexes for high performance.      |
| [[Glue]]           | ETL                          | Serverless. Out-of-the-box integration for Athena. ETL.             |
| [[Lake Formation]] | Data Lake                    | Serverless. Fine-grained permissions.                          |
| [[QuickSight]]     | BI Analytics Visualization   | Users and Role are separately managed from [[IAM]].            |
| [[Athena]]         | SQL for S3                   | Serverless. Federated query. Glue. Cost optimization - no etl. |
| [[Data Pipeline]]  | Workflow Automation with ETL | Supports [[Hybrid Cloud Architecture]]                         |
| [[EMR]]            | Map Reduce                   | Scalable data pipelines, Big Data                              |
| [[OpenSearch]]     | Search                       | Unstructured data search                                                               |

** Redshift versus Athena**
![[redshift-spectrum-athena-comparison-table.png|512]]
Fig. Comparison
