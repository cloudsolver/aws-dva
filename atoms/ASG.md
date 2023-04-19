### Summary of ASG
EC2 Autoscaling Groups are Regional Constructs. Supply AMI to ASG to launch instances.
[doc](https://aws.amazon.com/ec2/autoscaling/)
### ASG Details
- Set desired, minimum and maximum capacity.
- Dynamic Scaling: Tracks [CloudWatch](CloudWatch) and acts when it is in ALARM.
- #WellArchitected For Fault tolerance requires the minimum number of [[EC2]] instances in each [[AZ]] that enables [[Resilient Architectures]] on AWS.
- EC2 instance launched from the oldest launch configuration is terminated first.
| Scaling         | Description                                                                                                        |
| --------------- | ------------------------------------------------------------------------------------------------------------------ |
| Simple          | The first scaling policy on AWS. No fine-grained controls. CloudWatch alarm can trigger a `%` increase in capacity |
| Target Tracking | Recommended - especially for CPU metrics. Set the target metric and the scaling group expands or contracts to meet it.                                       |
| Step            | Useful when ASG continues to react to alarms with no cool down wait.                                                                                                                   |

	- Target Tracking Scaling: Amazon [[CloudWatch]] metric and target value.
	- Step Scaling: Update capacity based on a SET of scaling adjustments.

- Deleting an ASG terminates EC2 instances
- ASG can be configured with [[SNS]] to send notifications on scaling events.
ASG ensures EC2 instances are within a range (minimum, maximum capacity).
It can scale out EC2 instances to match the load, and scale in when load decreases.
Automatically registers new instances to a load balancer.
Recreate an EC2 instance if one is terminated or unhealthy.
- There is no cost for ASG itself.
- ASG also supports Lifecycle hooks - that can take a snapshot of an EBS volume if an EC2 instance gets terminated, and restore it to another AZ via another lifecycle hook. [more on Lifecycle Hooks](https://docs.aws.amazon.com/autoscaling/ec2/userguide/lifecycle-hooks.html)

A Launch Template is required for an ASG.
- [[AMI]] + Instance Type
- EC2 User Data
- EBS Volumes
- Security Groups
- [SSH](SSH.md) Key Pair
- IAM Roles for EC2 Instances
- Network + [[Subnet]] 
- [ELB](ELB.md) Info
- Initial Capacity, Min and Max Size.
- Scaling Policies.
- [[CloudWatch ]] Alarms can trigger a scaling request to ASG.
- With launch templates, you can provision capacity across multiple instance types using both **On-Demand Instances** and **Spot Instances** to achieve the desired scale, performance, and cost. Hence this is the correct option.

#### Quiz
#Q  You have an ASG and an [NLB](ELB.md#NLB). The application on your ASG supports the HTTP protocol and is integrated with the Load Balancer health checks. You are currently using the TCP health checks. You would like to migrate to using HTTP health checks, what do you do?
(a) Migrate to an Application Load Balancer
(b) Migrate the health check to HTTP
Answer: Both answers are correct. Remember, that NLB supports HTTP health checks.

#### References for ASG
1. https://docs.aws.amazon.com/autoscaling/ec2/userguide/scale-your-group.html
2. https://aws.amazon.com/autoscaling/
---
Created on 2023-03-10 21:55