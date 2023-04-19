Redundant Array of Inexpensive Disks uses parity, striping and mirroring to enable write performance, high availability, fault tolerance and other benefits.
[source](https://www.spiceworks.com/tech/data-management/articles/what-is-raid-storage/)

> Striping: Data is split across many drives.
> Parity: Data recovery mechanism for fault tolerance.
> Mirroring: Data is copied for redundancy for faster times to recover.

### RAID 0
- Two drives as one logical volume.
- High write performance due to concurrent writes.
- Not fault tolerant - if a drive fails there will be data loss.
- Recommended for EBS by AWS.
- Multiple RAID 0 - will increase performance
#Q The application writes many temporary files during the data processing. The application requires a high-performance storage solution for the temporary files. **What would be the fastest storage option for this solution?**
(a) Multiple EFS volumes with Max I/O performance
(b) Multiple S3 buckets with transfer acceleration 
(c) Multiple EBS volumes with provisioned IOPS
(d) Multiple Instance Store volumes with software RAID 0
### RAID 1
- Two drives with half the storage capacity.
- Data is mirrored
- 2x read and 1x write.
- One operational disk makes the data available 
![[RAID 0 v RAID 1.png]]
Fig. RAID 0 and RAID 1
### RAID 5
- Three drives adds consistency ; one drive used for parity
- RAID 5 surpasses RAID 1 and RAID 0 in fault tolerance
- More storage than RAID 1
- Any drive is hot swappable
![[RAID 5.png]]
Fig. RAID 5
### RAID 6
- RAID 5 + additional drive for double parity aka "Double Parity RAID"
- Permits two drive failures with no data loss
- Write performance is slower
![[RAID 6.png]]
Fig. RAID 6
### RAID 10
- Two RAID 1 sets inside one RAID 0 aka "RAID 1 + 0"
- Reliability, stability and performance but expensive
- Stripes data across mirrored pairs
- A standard four-disk RAID 10 setup can only withstand **one drive failure in each mirrored pair of disk drives**.
![[RAID 10.png]]
Fig. RAID 10
