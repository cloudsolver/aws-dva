## RDS Summary
Amazon RDS is a managed RDBMS service that supports various relational database engines. RDS supports, single AZ read-replicas for read scalability, Multi-AZ deployments for HA, and cross-region replication for DR.


### Engines
- PostgreSQL
- MySQL
- MariaDB
- Oracle
- Microsoft SQL Server
- Aurora 
	- PostgreSQL
	- MySQL
### Features
- Automated provisioning, OS patching.
- Continuous backup on gb2 or io1 and Point-in-time restore.
- Monitoring Dashboards.
- Read replicas for improved read performance.
- Multi AZ setup for DR.
- Maintenance Windows for upgrades.
- Scaling capability vertical or horizontal.
#### Storage Auto Scaling
- Scale storage automatically so the DB won't run out of free space.
- Set the `Maximum Storage Threshold`
- Useful for applications with _unpredictable workloads_.
- Automatically modify storage:
	- Free storage is <10% of allocated storage.
	- Low-storage lasts at least 5 mins.
	- 6 hours have passed since last modification.
### Constraints
- No [[SSH]] access to the database engine.
	- Unless you opt for [[RDS Custom]] where you get access to EC2 instance.
- Enhanced Monitoring needs to be enabled
	- To monitor how the different processes or threads on a DB instance use the CPU, including the percentage of the CPU bandwidth and total memory consumed by each process

### RDS Read Replica
[[RDS Read Replicas]]

### RDS Multi-AZ
[[RDS Multi-AZ Deployments]]

### RDS Cross Region Replication
![RDS Cross Region Replication](RDS%20Cross%20Region%20Replication.md#Summary)

## RDS Backup
![RDS Backup](RDS%20Backup.md#RDS%20Backup%20Summary)

## RDS Security
[[RDS Security]]

### Monitoring and Audit Logs
- CloudWatch logs for longer retention.
- Enhanced RDS Monitoring Provides:
	- RDS Child Processes
	- OS Processes

![[RDS Proxy]]

## Quiz
#Q You need to store long-term backups for your Aurora database for disaster recovery and audit purposes. What do you recommend?
1. Enable Automated Backups
2. Perform On-Demand Backups
3. Use Aurora Database Cloning
	Answer: Automated backups have a maximum retention of 35 days. However, on-demand backups can have any retention period.
	
#Q You would like to create a disaster recovery strategy for your RDS PostgreSQL database so that in case of a regional outage the database can be quickly made available for both read and write workloads in another AWS Region. The DR database must be highly available. What do you recommend?
1. Create a Read Replica in the same region and enable Multi-AZ on the main database.
2. Create a Read Replica in a different region and enable Multi-AZ on the Read Replica.
3. Create a Read Replica in a different region and enable Multi-AZ on the Read Replica
4. Enable multi-region option on the main database.
Answer: There must be another Region ready to take on the load. Probably not possible to set up a multi-region option. However, enabling Multi-AZ on the Read Replica in another region is a good option for DR. We don't need HA and Read Scalability - just need DR.
## References
1. https://aws.amazon.com/rds/faqs/