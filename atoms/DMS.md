Data Migration Service sets up a continuous replication from source to target. Move data without development effort. #AWSService 

![[DMS Continuous Replication.png|512]]
Fig. Continuous Replication Architecture. SCT on-prem

CDC - Change Data Capture is supported within the AWS EC2 replication instance, SCT is run on-prem. #BestPractice 

SCT - Schema Conversion Tool can transform the database schema e.g. from Oracle to MySQL. You don't need this if the database engine is the same. SCT is installed on-premises.

### Database Migration
- RDS to Aurora Migration
	- MySQL (external)
		- mysqldump to Aurora. Takes time but no S3.
		- percona to S3, then S3 import to Aurora. Requires 3rd party tool.
		- DMS if both are running
	- MySQL (RDS)
		- DB Snapshot on RDS, Restore on Aurora
		- Aurora Read Replica from RDS; wait until lag is zero; then promote Aurora Read Replica to master. Time and cost is high.
	- PostGreSQL
		- RDS Snapshot, Restore on Aurora.
		- Import from S3 using `aws_s3` Aurora extension
- Database Migration Service (DMS) can be used to replicate data from Amazon [[S3]] to Amazon [[Kinesis]] Data Streams and [[Redshift]].
 
https://aws.amazon.com/dms/