## Cost Optimized
1. Design cost-optimized storage solutions.
	1. Access options: [[S3]] with Requester Pays object storage.
	2. AWS cost management service features: Cost Allocation Tags, Multi-Account billing.
	3. AWS Cost Management tools with appropriate use cases: AWS Cost Explorer, AWS Budgets, AWS Cost and Usage Report.
	4. AWS storage services with appropriate use cases: Amazon FSx, Amazon [EFS](EFS.md), Amazon S3, Amazon [EBS](EBS.md).
	5. Backup strategies.
	6. Block storage options: HDD volume types, SSD volume types.
	7. Data lifecycles.
	8. Hybrid storage options: [DataSync](DataSync.md), Transfer Family, Storage Gateway.
	9. Storage access patterns.
	10. Storage tiering: Cold Tiering for object storage.
	11. Storage types with associated characteristics: Object, File and Block.
	12. Skills:
		1. Designing appropriate storage strategies: Batch uploads to AWS S3 compared with individual uploads.
		2. Determining the correct storage size for a workload.
		3. Determining the lowest cost method of transferring data for a workload to AWS storage.
		4. Determining when storage auto scaling is required. 
		5. Managing S3 object lifecycles.
		6. Selecting the appropriate backup and archival solution.
		7. Selecting the appropriate services for data migration to storage services
		8. Selecting the appropriate storage tier
		9. Selecting the correct data lifecycle for storage.
		10. Selecting the most cost-effective storage service for a workload.
2. Design cost-optimized compute solutions.
	1. AWS cost management service features: Cost Allocation Tags, Multi-Account Billing.
	2. AWS Cost Management tools with appropriate use cases: Cost Explorer, AWS Budgets, AWS Cost and Usage Report.
	3. AWS [[Global Infrastructure]]: Availability Zone, Regions.
	4. AWS purchasing options: Spot Instances, Reserved Instances, Savings Plans.
	5. Distributed compute strategies: Edge processing.
	6. Hybrid compute options: AWS Outposts, Snowball Edge.
	7. Instance types, families, and sizes: Memory optimized, compute optimized, virtualization.
	8. Optimization of compute utilization: [[Containers]], [[Serverless Architecture UseCase]] computing, [[Microservices]].
	9. Scaling strategies: Auto scaling, hibernation.
	10. Skills:
		1. Determining an appropriate load balancing strategy: ALB (Layer 7) , Network Load Balancer (Layer 4) compared with Gateway Load Balancer.
		2. Determining appropriate scaling methods and strategies for elastic workloads (Horizontal compared with Vertical, [EC2](EC2.md) Hibernation).
		3. Determining cost-effective AWS compute services with appropriate use cases: Lambda, [EC2](EC2.md), Fargate.
		4. Determining the required availability for different classes of workloads: production workloads, non-production workloads.
		5. Selecting the appropriate instance family and size for a workload.
3. Design cost-optimized database solutions.
	1. AWS cost management service features: Cost Allocation Tags, Multi-Account Billing.
	2. AWS Cost Management tools.
	3. Caching Strategies.
	4. Data retention policies.
	5. Data capacity planning.
	6. Data connections and proxies.
	7. Database engines with appropriate use cases: heterogeneous migrations, homogeneous migrations.
	8. Database replication: read replicas.
	9. Database types and services: relational compares with non-relational, Aurora, [[DynamoDB]].
	10. Skills:
		1. Designing appropriate backup and retention policies: snapshot frequency.
		2. Determining an appropriate database engine: MySQL versus PostgreSQL.
		3. Determining cost-effective AWS database services with appropriate use cases: DynamoDB compares with Amazon RDS, serverless.
		4. Determining cost-effective AWS database type: time series format, columnar format.
		5. Migrating database schemas and data to different locations and different database engines.
		   
1. Design cost-optimized network architectures.
	1. AWS cost management service features and tools.
	2. Load balancing concepts: ALB.
	3. [[NATGW]]s: NAT instance costs compared with NAT gateway costs.
	4. Network connectivity: Private lines, dedicated lines, VPNs.
	5. Network routing, topology, and peering: AWS Transit Gateway, [[VPC]] peering.
	6. Network services with appropriate use cases: DNS.
	7. Skills:
		1. Configuring appropriate NAT gateway types for a network: Single shared NAT gateway compared with NAT gateways for each AZ.
		2. Configuring appropriate network connections: [[DX]] compared with VPN compared with Internet.
		3. Configuring appropriate network routes to minimize transfer costs: [Region](Region.md) to [Region](Region.md), AZ to AZ, private to public, Global Accelerator, [[VPC]] endpoints.
		4. Determining strategic needs for content delivery networks and edge caching.
		5. Reviewing existing workloads for network optimizations.
		6. Selecting an appropriate throttling strategy.
		7. Selecting the appropriate bandwidth allocation for a network device: single VPN compared with multiple VPN, [[DX]] speed.
