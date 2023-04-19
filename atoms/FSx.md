## Summary
Amazon FSx is a managed File System service for popular clustered distributed file systems. Support FSx file systems: NetApp ONTAP, OpenZFS, Windows File Server with [[AD]] support, and [[Lustre]] for [[HPC]]. #AWSService 
## Amazon FSx Details
![](FSx_file_systems.png)

#### FSx for Windows 
- Supports SMB, NTFS, AD integration, ACLs, user-quotas and Linux mountable on EC2. Supports Microsoft's [[DFS]] and multi-AZ. Data is backed up to S3.
#### FSx for Lustre
- [Lustre](Lustre.md) is used for [[ML]], [[HPC]], Video processing, Financial Modeling or other sub-latency, high-throughput, scalable workloads. Seamless integration with [[S3]] - read and write to it from FSx. VPN and [[DX]] are support for [[Hybrid Cloud Architecture]]
	- Scratch File System: Performance over durability and availability. High **Bursts** 6x faster.
#### FSx for NetApp ONTAP
- NetApp ONTAP is compatible with Linux, Windows, MacOS, VMWare Cloud on AWS, [[Workspaces]], [[AppStream]], [[EC2]], [[ECS]], and [[EKS]].
	- Supports [[NAS]], [[NFS]], [[SMB]], [[iSCSI]] 
	- Snapshots, replication, low-cost, compression and data de-duplication.
	- Point-in-time instantaneous cloning. Useful for testing new workloads. #UseCase 
#### FSx for OpenZFS
Managed OpenZFS
	- [[NFS]] compatible, millions of IOPS.
	- Point-in-time instantaneous cloning just liske [[#NetApp ONTAP]]. 
	- Move workloads running on ZFS to AWS. #UseCase 
![](FSx_comparison_table.png)
## References

1.[When to choose FSx](https://aws.amazon.com/fsx/when-to-choose-fsx/)
