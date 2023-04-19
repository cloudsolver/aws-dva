## RDS Read Replicas Summary

Read scalability is achieved by asynchronously pushing data to up to five to fifteen read replicas within an [[AZ]], across AZs or Cross Region. 

## Introduction

Engines have native asynchronous replication features that are used to keep the read replicas up-to-date when changes are made to the primary. Enhanced performance, increased availability and secure.

![|250](https://d1.awsstatic.com/asset-repository/read-replicas-scaling-disaster-recovery.3b8da7093daeb1e87426225caf49e32efe7ae01a.png)
- Read replicas are supported within a region, across-regions as well as on-premises. [[Hybrid Cloud Architecture]]
- Maximum 5 Read Replicas for Oracle and Microsoft. 
	- Max 15 for MySQL, Maria and PostgreSQL.
- A read-replica as multi-AZ DB instance can be created even if the source database is not a multi-AZ instance.
- Applications must be updated to a read-replica connection string.
- Replication is asynchronous.
- Replicas can be promoted to their own DB - it can be outside the replication scheme and become a primary.
- Encryption at rest with [[KMS]] can be enabled.
- RDS read-replicas within region is free. Cross region traffic will be charged.
- Zero downtime to go from Single-AZ to Multi-AZ.

## Use Cases
- Reporting Application wants to run analytics. Create a read replica. Only for SELECT. Read scalability: create a read replica within AZ, cross AZ or Cross Region.
	- Asynch replication: eventually consistent.
- Disaster recovery: Master synchronously writes to standby database. One DNS name with automatic fail over. The read replica can be setup as Multi AZ for DR.
## References

- https://aws.amazon.com/rds/features/read-replicas/
