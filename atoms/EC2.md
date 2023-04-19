 [[EC2]]  Elastic Cloud Compute is a core #AWSService that runs virtual servers within a [[VPC]].
* Bootstrap with EC2 User Data - run once at instance first start.
	* Install updates, software, download files etc as sudo.
* Instance Naming Convention: m5.2xlarge m=instance class, 5=generation, 2xlarge=size of instance within class.
* General Purpose: Web-server, application servers, 
* **Compute Optimized**: Media transcoding, batch processing, high performance web servers, high performance computing (HPC), machine learning, scientific modeling and dedicated gaming server.
* **Memory Optimized**: High performance, relational and non-relational database, distributed web scale cache stores, In-memory databases optimized for BI, applications performing real-time processing of big unstructured data.
* **Storage Optimized**: High throughput for sequential reads and writes. 
* Use this website to checkout the EC2 Instance types https://instances.vantage.sh/ #tip 
* [[CloudWatch]] can monitor CPU, Network and Disk but not Memory Usage. To monitor memory you must install an CloudWatch Agent.
### EC2 Connection

- [[SG]] is a firewall for EC2. 
- You can connect to EC2 via [[EC2 Instance Connect]] or [[SSH]] assuming the [[SG]] has been setup.
- EC2 can assume a role to use other services #BestPractice Do not run `aws configure` into an EC2 instance. [IAM Role](IAM#IAM%20Role) should be used : attach the role to the EC2 instance. Based on the role, you can run AWS commands such as `aws iam list-users` from within the EC2 instance.
- EC2 instances always get assigned an IPv4 within the CIDR range of the subnet.
- EC2 instance must have a public IP address in order to connect to the Internet.

## EC2 Instance Purchasing Options
* EC2 On-Demand Instances
	* Highest cost
* EC2 Reserved Instance
	* Reserved Instance: 72% discount. 
		* 1 year or 3 year
		* Instance Type, [Region](Region.md), Tenancy, OS
		* Can be sold if unused.
	* Convertible Reserved Instance
		* Can change the EC2 instance type, instance family, OS, scope and tenancy.
		* Up to 66% discount.
		* Can not be sold at the Reserved Instance Marketplace.
	* Scheduled Reserved Instances
		* For regularly scheduled daily, weekly and monthly workload for a specific start time and duration. [more](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-scheduled-instances.html)
* Savings Plan
	* Get a discount based on long-term usage (up to 72% - same as RIs)
	* Commit to billable usage for 1 or 3 years.
	* Usage beyond the commitment defaults to On-Demand price.
	* Flexibility: Instance size within family, OS, and tenancy e.g. default, dedicated, host.
* [[EC2 Spot Instance]] Supports massive discounts up to 90%.
* EC2 Dedicated Hosts
	* Physical server with EC2 instance capacity.
	* #UseCase compliance requirements, server-bound software license e.g. per-socket, per-core or BYOL.
* EC2 Dedicated Instances
	* Hardware shares with instances of the same account.
	* No control over instance placement.
* EC2 Capacity Reservation
	* Reserve On-Demand instance capacity in a **specific AZ** for any duration.
	* You always have access to EC2 capacity when you need it.
	* No time commitment.
	#UseCase EC2 instances are guaranteed to be available when needed.

- You can assign an [[ElasticIP]] to your instance. Only one per EC2 instance.

When you launch a new EC2 instance, the EC2 service attempts to place the instance in such a way that all your instances are spread out across underlying hardware to minimize correlated failure. You can use [[Placement Groups]] to influence the placement of a group of interdependent instances to meet the needs of your workload. 

### EC2 Storage Types
### Instance Storage
- Ephemeral / Instance Storage on EC2 provides the highest performance >1M IOPS in some cases. However it is not durable across restarts. Good for temporary high-performance data. #performant  #UseCase 
#### Volume Storage
- [[EBS]] volumes can be attached to EC2 instances with up to 64K IOPS. Local to AZ. Backup and restore to another AZ is possible and can be automated to support HA. #resilient 
#### File Storage
- [[EFS]] Elastic File Systems can be used for file base storage. Multiple instances, in fact 100s of instances can use the file storage.

## EC2 Hibernate
* RAM state is written to a file in the root [[EBS]] volume. The root [EBS](EBS.md) volume must be encrypted. 
* Running => Hibernate => Hibernation => Start => Running
* #UseCase long-running processing, saving time to bootup
* Supported C, I, M, R, T . Not supported on bare metal instances. [[AMI]] - many.
* Root Volume - must be [EBS](EBS.md), encrypted, not instance store, and large. 
* 150GB, 60 days limit.
* From OS pov `uptime` will count time elapsed during hibernation.

### Scaling EC2 Horizontally
- [[ASG | Auto-Scaling Group]] with appropriate launch configurations and scaling policies can be used to scale. #performant 