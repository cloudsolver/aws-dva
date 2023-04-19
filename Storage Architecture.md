### Summary of Storage Architecture
There are various storage options.
### Storage Architecture Details
|Need|Solution|Constraints|
|---|---|---|
| Object Storage | [[S3]] | Updates require full replacement  |
| Archival | [[Glacier]] | Lifecycle entry only  |
| Network Volume for [[EC2]] | [[EBS]] | Limited horizontal scalability |
| [[EC2]] Instance Store | [Instance Storage](EC2.md#Instance%20Storage) | Ephemeral - durability |
| Network File System for POSIX | [[EFS]] | Not suitable for OS |
| Network File System for Win | [FSx for Windows](FSx.md#FSx%20for%20Windows) | |
| Network File System for Linux with HPC | [FSx for Lustre](FSx.md#FSx%20for%20Lustre) | Lustre admin is complex |
| High OS compatibility | [FSx for NetApp ONTAP](FSx.md#FSx%20for%20NetApp%20ONTAP) | Lower throughput compared to Lustre |
| Managed ZFS File System | [FSx for OpenZFS](FSx.md#FSx%20for%20OpenZFS) | |
| Hybrid Cloud Storage Architecture backed by S3 & FSx File Gateway, Volume Gateway (cache & stored), Tape Gateway  | [Storage Gateway](Storage%20Gateway.md) | Requires on-prem administration | 
| FTP, FTPS, SFTP interface on top of Amazon S3 or Amazon EFS   | [Transfer Family](Transfer%20Family.md) | Costs can get high |
| Multi-Cloud, Hybrid Cloud, Intra-AWS Data Sync with meta-data preservation | [DataSync](DataSync.md) | Setup and admin required |
| Move large amounts of data to the cloud faster than the Internet | [Snow Family](Snow%20Family.md) | Tradeoff cost versus time  |

#### References for Storage Architecture
1. https://aws.amazon.com/architecture/storage/
---
Created on 2023-03-09 17:10