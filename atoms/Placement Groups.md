### Placement Group Types
Cluster, Partition and Spread [[EC2]] [placement groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html) are offered. Placement groups influences placement of group of interdependent instances.
### Cluster 
- Low-latency for tightly-coupled node-to-node communications highest networking performance. e.g. HPC. Max performance, least reliable.
- A cluster placement group can span peered virtual private networks ([[VPC]]s) in the same Region.
- [Enhanced Networking](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/enhanced-networking.html) on linux uses single root I/O virtualization [[SR-IOV]] to provide high-performance networking capabilities. Note: T2 instances don't support it. There is not extra charge.
* Use a single launch request to launch all the instances and use the same instance type for all instances.
* There is no limit set for the number of instances allowed to run. If there are issues adding more instances - you can try to restart the cluster/placement - AWS will try to find a rack that can accommodate the new number.
 ![[cluster_placement_group.png]]
 Fig. Cluster Placement Group
* #Q You have an application performing big data analysis hosted on a fleet of EC2 instances. You want to ensure your EC2 instances have the highest networking performance while communicating with each other. Which EC2 Placement Group should you choose?
* Answer: If performance over HA is required. Go for Cluster Placement Group.

### Partition
- Large distributed and replicated workloads such as Hadoop, Cassandra and Kafka can run in partitions that each has its own set of racks. Each partition runs multiple instances.
- You can see which instances are in which partitions - this enables topology-aware applications such as HDFS, HBase and Cassandra to make intelligent data replication decisions for increasing data availability, and durability. 7 partitions per Availability Zone.
![[partition_placement_group.png]]
Fig. Partitions (Racks) for partition-aware workloads

### Spread
Reliability and reduction of correlated failures by placing instances across distinct underlying hardware. Minimize failure worst performance.
* Spread placement groups are suitable for mixing instance types or launching instances over time.
* Seven instances can be launched with each in its own rack that has its own network and power source in an [[AZ]]. Max 7 instances.
* ![[spead_placement_group.png]]