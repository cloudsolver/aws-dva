## Summary
AWS offers four categorizes of EBS volumes: GP, IO, ST, and SC. GP is general purpose, IO is provisioned IOPS, ST is throughput optimized and SC is cold HDD volume.

Six types, grouped in 4 categories. Size, throughput and IOPS are differentiated.

## Volume Categories
### **gp2/gp3 (SSD) : General Purpose**

- General purpose cost-effective low-latency SSD volumes.
#UseCase general workloads with a balance of price and performance. Boot volumes. Dev and test environment.
- gp3: 3K IOPS baseline and 125MiB/s. Increase 16 K IOPS and 1000 MiB/s (independent).
 - gp2: 3K IOPS burst. IOPS and Size are linked: 3 IOPS per GB upto 16K IOPS: 5334 GB (5TB) maxes IOPS (dependent). #tip No need to increase gp2 beyond 5TB to increase IOPS.
### **io1/io2 (SSD) : Fasted Provisioned IOPS**
- Only one that supports multi-attach. Max 16 instances.
- Highest performance SSD volumes for mission critical and high-throughput workloads. #performant 
- #UseCase Mission-critical low-latency or high-throughput workloads. Boot volumes.
- io1 and io2 Size: 4GB-16TB. Max: 64K IOPS only for Nitro EC2; 32K IOPS for others. io2 is better than io 1 because you get more durability and more IOPS per GiB. #UseCase More than 32K IOPS with Nitro EC2.
- io2 Block Express (4GiB - 64TiB) sub-second latency. Max IOPS: 256K GiB ratio 1000:1
- #UseCase Multi-attach with full read/write: Same EBS volume to multiple EC2 instances in the same AZ. Up to 16 EC2 instances. Must use cluster-aware file system
- #UseCase Achieve higher application availability in clustered Linux applications (e.g. Terradata). 
- #UseCase Applications must manage concurrent write operations.
	
### st1 (Throughput HDD)
- Low cost HDD vol. Cannot be boot volume.
- #UseCase Frequent accessed, throughput sensitive. Big Data, Data Warehouses, Log Processing.
- Size: 125 GiB to 16 TiB. Max IOPS 500 (500MiB/s)
### sc1 (Code HDD)
- Lowest cost HDD vol. Cold HDD. #CostOptimized 
- #UseCase Less frequently accessed. Archive data.
- 250 IOPS max.

### Quiz
#Q A company is currently running a production workload on AWS that is very I/O intensive. Its workload consists of a single tier with 10 c4.8xlarge instances, each with 2 TB gp2 volumes. The number of processing jobs has recently increased, and latency has increased as well. The team realizes that they are constrained on the IOPS. For the application to perform efficiently, they need to increase the IOPS by 3000 for each of the instances. Which of the following options will meet the performance goal MOST cost effectively?
(a) Change the type of the EBS volume to io1 and set provisioned IOPS to 9000.
(b) Increase the size of the gp2 volumes in each instance to 3TB.
(c) Create a new Amazon EFS and mount it across 10 instances.
(d) Create a new S3 bucket and move all the data to this new bucket.
Answer; The concept is that gp2 capacity and IOPS are tightly coupled. Increases at 3IOPS/GB.

## References
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/hdd-vols.html