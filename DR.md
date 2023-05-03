## Summary
DR is the process of preparing for and recovering from a disaster. A resilient architecture will have a robust disaster recovery plan. DR is usually a part of a  business continuity plan. #resilient #WellArchitected 

### Shared Responsibility
[[Shared Responsibility Model]]

## Disaster Recovery Details
Disaster Recovery architecture is different than a High Availability architecture. It can use multiple methods and there are various types.

### Measures

![DR|500](https://d2908q01vomqb2.cloudfront.net/fc074d501302eb2b93e2554793fcaf50b3bf7291/2021/04/02/Figure-1.png)

[[RPO]] is the recovery point objective: measures the acceptable amount of data loss. It is the maximum acceptable amount of time since the last data recovery  
point. This objective determines what is considered an acceptable loss of data between the last recovery point and the interruption of service and is defined by the organization.

[[RTO]] is the recovery time objective: measures the acceptable amount of time elapsed before service is restored.

![[DR Availability.png|256]]
Fig. Measures

![[dr_availability_formula.png]]
Fig. Availability


### RTO, RPO mapped to DR Architecture
![[DR Strategy with RPO and RTO.png]]
Fig. RTO RPO relative to DR Strategy

### Backup and Restore 
Store data off site. 
IT infrastructure is not backed up.
Support point in time recovery.
Backup as a Service
- Third party is contracted to back up data but not infrastructure.
### Pilot Light
Data is replicated and backup of databases, object stores are always on. However, code, infrastructure-as-code is are loaded but "switched off". These are "switched on" for DR testing or during a regional disaster. Core infrastructure on the cloud can be launched when needed without having to always pay for it.
### Warm Standby
- Resources running on a failover site have continuous backups coming in.
- Infrastructure resources are in a staging environment.
- Upon failover, these resources are scaled up.
### Multi-Site
- Low RPO, Low RTO.
- Expensive and complex architecture.
- Cold Site
		- Business operations can continue in rarely use facility but this must be complemented with another data and infrastructure backup and restoration.
	- Hot Site
		- Up-to-date copies of data allows dramatic reduction in down time.
	- DRaaS
		- Disaster or Ransonware attack - the organization's infrastructure is moved to the organizations computer processing to enable business continuity.
	- Virtualization
		- Offsite virtual machines with synchronized data.
	- Data-center disaster recovery
		- Physical protections to recover faster e.g. fire suppression, backup power etc.
	- Point-in-time copies
		- Entire database is copied.
	- Instant recovery
		- Snapshot an entire VM without database copies.

#### S3 Global Accelerator Disaster Recovery and multi-region resiliency

You must be able to rely on your network to be available. You might be running your application across multiple AWS Regions to support disaster recovery, higher availability, lower latency, or compliance. If Global Accelerator detects that your application endpoint is failing in the primary AWS Region, it instantly triggers traffic re-routing to your application endpoint in the next available, closest AWS Region.

#### Aurora Global Database
 [[Aurora]] global databases span multiple AWS Regions, enabling low latency global reads and providing fast recovery from the rare outage that might affect an entire AWS Region. An Aurora global database has a primary DB cluster in one Region, and up to five secondary DB clusters in different Regions.

With the warm standby strategy the application can handle traffic (at reduced capacity levels) immediately so this will reduce the RTO.

**References**

1. https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-workloads-on-aws.html?did=wp_card&trk=wp_card
2. https://aws.amazon.com/blogs/architecture/disaster-recovery-dr-architecture-on-aws-part-i-strategies-for-recovery-in-the-cloud/
3. https://docs.aws.amazon.com/pdfs/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-workloads-on-aws.pdf#disaster-recovery-workloads-on-aws
4. https://www.vmware.com/topics/glossary/content/disaster-recovery.html