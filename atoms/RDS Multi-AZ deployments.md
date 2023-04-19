## Summary

Multi-AZ deployments offers one primary and a secondary or one primary with two readable standbys that spans at least 2 AZs to enable High Availability through automatic failover to standby or read replica (Aurora) when a problem is detected.
## About
RDS automatically creates a primary database, and sets up a secondary database that it replicates to synchronously. Automatic failover within 35 secs and zero data loss.

- Supports HA with active-passive.
- Sync Replication.
	- Aurora: Async
- Only Primary is active 
	- Aurora: Multi-master.
- Automated backups are taken from standby
	- Aurora: from shared storage layer
- Always span at least 2 AZ 
- DB engine version upgrades happen on primary
	- Aurora: all instances are updated together.
- Automatic failover to standby
	- Aurora: 
- The canonical name record - CNAME is switched from the primary to standby instance.
![[Pasted image 20230417174943.png]]
Fig. Multi-AZ versus Read Replica
### _Multiple-AZ with two readable standbys_
Available for PostgreSQL and MySQL.
* Standbys serve as failover targets as well as serve read traffic.
* Read capacity is determined by the overhead of write transactions from the primary. #tip 
* Lower latency with faster transaction commits compared to one standby.
* Uses 2-of-3 write quorum.
## References
 - https://aws.amazon.com/rds/features/read-replicas/
 - https://aws.amazon.com/rds/features/multi-az/
 - https://youtu.be/_MROZtLtCcA