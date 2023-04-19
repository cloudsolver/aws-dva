## Summary
Offline large data transfer without network to and from AWS and also supports Edge Computing. Snowcone, Snowcone SSD, Stand-alone Snowball, and Snowball Edge are typically also used for Edge Computing and batch data processing. Snow Mobile is used for data center migrations at Exabyte scale.

## Snow Family Details
Snow Family of products cannot import data directly to [Glacier](S3%20Storage%20Class.md#Glacier) The path to Glacier must be traveled through [S3](S3.md)
![](snowball_glacier_process.png)

Note: Export data out of Snowball into S3 is a requirement, from there you can import it into [[FSx]] or any other storage based on the business need.
#### Snowcone 
- **Snowcone** –2 vCPUs, 4 GB RAM,  8 TB HDD.
- **Snowcone SSD** – 2 vCPUs, 4 GB RAM,  14 TB SSD
- You can run workloads on EC2 within these devices.
- [[DataSync]] comes preinstalled.

#### Snowball
* < 80 PB of storage.
* Snowball Edge can be Cluster for more storage, typically 45TB per node in a leader-less cluster. Up to 15 devices.
* 
![](snowball_v_snowball_edge_table.png)
#### Snowmobile
- <100 PB of storage per snowmobile.
- Exabyte data transfer
![Snow](snow_family_table.png)

## References

1. [AWS SnowFamily](https://docs.aws.amazon.com/snowball/index.html)
2. [AWS Snowcone](https://docs.aws.amazon.com/snowball/latest/snowcone-guide/snowcone-what-is-snowcone.html)