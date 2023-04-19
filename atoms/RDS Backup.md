## RDS Backup Summary
RDS offers snapshot backup and restore from S3, Aurora offers Database cloning that is faster and more cost effective.
## About
### Automated Backups and Point-in-time Restores
- 5 Minutes RPO - data is backed up every 5 minutes. Can be retained from 0-35 days.
- Daily full backups of the database. #resilient 
- Snapshot a database that you don't want to use for a long period and then restore when you need it - because RDS will charge you for storage. #tip #CostOptimized
- Snapshots can be copied across Amazon accounts, regions and and within a region. 
- Restore a full database from a snapshot.
- Aurora Backups
	- Cannot be disabled like RDS can.
	- Manual DB Snapshots.
- Restoring RDS/Aurora backup or a snapshot to create a new DB.
- Restoring MySQL RDS database from S3 is simple.
- Restoring MySQL Aurora RDS requires Percona XtraBackup to restore to a new Aurora cluster.
- Aurora Database Cloning 
	- is an alternative to snapshot and restore
	- faster and more cost effective. #CostOptimized 
	- useful to create a 'staging' database without impacting prod. #UseCase 
## References

1. https://aws.amazon.com/rds/features/backup/
