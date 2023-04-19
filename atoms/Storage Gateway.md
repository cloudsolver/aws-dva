### Summary of Storage Gateway
Bridges on-premise data with cloud data on AWS as an essential component of a [Hybrid Cloud Architecture](Hybrid%20Cloud%20Architecture.md) #AWSService 
### Storage Gateway Details
On-premises environment can host File, Volume, and Tape gateway for various workloads. [[NFS]] and [SMB](SMB) protocols would connect internal file shares with the File Gateway on-prem. Application Servers would use [iSCSI](iSCSI) to connect to a Volume Gateway on-prem. Backup application would use [[iSCSI#VTL]] to connect to a Tape Gateway. The gateways can be installed on virtualized or physical appliance on-premise.
![512](storage_gateway_on_prem_arch.png)
Useful for [[DR]], [AWS Backup](AWS%20Backup.md) and restore. Tiered storage with on-premises [cache](Cache.md) and local-latency file access.

Provide on-premises applications with access to virtually unlimited cloud storage. Fill [[S3]] will incoming data from on-prem to form a [[DataLake]], modernize file sharing for #CostOptimized architecture and #OperationallyExcellent 

#### S3 File Gateway
- Most recently used files are cached on the File Gateway locally on-premises.
- S3 Buckets are accessible using NFS and SMB protocols with AD for user auth.
- Transition to Glacier via LifeCycle Policies.


#### FSx File Gateway
- Native access to Amazon FSx for Windows File Server
- Advantages: Cache, Windows native compatibility.

#### Volume Gateway
- Is not pre-provisioned - pay-per-use and compressed transfer and storage saves cost.
- Block storage using iSCSI protocol backed by S3.
- Backed by EBS snapshots to help restore on-premises volumes.
- Cached volumes offer low latency to most recent data.
- Stored volumes: entire dataset is on premises, scheduled backups to S3.
#### Tape Gateway
- On-prem Virtual Tape Library (VTL) is integrated with [Glacier](Glacier.md) **Deep Archive** Storage Class. 
#### Storage Gateway Hardware Appliance
- On-Premise Virtualization Alternative is to buy a Storage Gateway Hardware Appliance.
- Works with File, Volume and Tape Gateways.

### DataSync versus Storage Gateway
Although you can copy data from on-premises to AWS with Storage Gateway, it is not suitable for transferring large sets of data to AWS. Storage Gateway is mainly used in providing low-latency access to data by caching frequently accessed data on-premises while storing archive data securely and durably in Amazon cloud storage services. Storage Gateway optimizes data transfer to AWS by sending only changed data and compressing data. To move large data sets to AWS from on-prem it is best to use [[DataSync]] which i 10x faster than most open source products.


#### References for Storage Gateway
1. https://aws.amazon.com/storagegateway/
2. https://aws.amazon.com/storagegateway/faqs/?nc=sn&loc=6
3. https://aws.amazon.com/storagegateway/faqs/?nc=sn&loc=6

---
Created on 2023-03-09 14:14