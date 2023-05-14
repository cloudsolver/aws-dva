### Summary of ECS
Elastic Container Service requires you to provision and maintain the EC2 instance. #AWSService 

### ECS Details

#Q How does ECS Autoscale? 
See [[ECS Autoscaling]]. 
**Answer**: ASG scales tasks.

---
#Q How does ECS perform rolling updates? 
See [[ECS Rolling Updates]].
**Answer**: ECS Service Scheduler replaces the current running version of the container with the latest version based on percentages of minimum and maximums.

#Q What is difference in cluster behavior if an instance is terminate when it was in the STOPPED state versus RUNNING?
Answer: If a RUNNING instance is terminated, it will be deregistered from the cluster. If an STOPPED instance is terminated, it will remain registered as a resource within the cluster.

---

ECS Deployment Configuration **Application Type**
 - Service to launch a group of tasks handling a long-running computing work e.g. web application
 - Task
 - launch a standalone task that runs and terminates e.g. batch job.

---
#Q How does EC2 launch type work?
See: [[ECS EC2 Launch Type]]
Answer:  EC2 behind, ASG, SG and open host ports. Task placement spread, random or binpack used.

---


 **Fargate Launch Type**
- No need to provision the infrastructure
- Create Task definitions, assign memory and CPU.
- To scale, just increase the number of tasks.

#Q Which [[ELB]] should be selected for ECS?  Based on the [evidence](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-load-balancing.html)  [[ALB]] is recommended and works for most use-cases. [[NLB]] recommended for high throughput / high performance use-cases or to pair it with AWS [[PrivateLink]]. 
**Answer**: Choose ALB, and in exceptions NLB.

#Q How can developers get the ECS environment setup without worrying about designing the underlying infrastructure?
See: [FAQ](https://aws.amazon.com/containers/copilot/faqs/) states that Copilot is a CLI that supports this.
Answer: By using AWS [[Copilot]] which is a command line interface (CLI) that you can use to quickly launch and manage containerized applications on AWS. It simplifies running applications on Amazon Elastic Container Service (ECS), AWS Fargate, and AWS App Runner.

### Solution Architectures with ECS

#Q How to share a mount point across EC2 and Fargate tasks in an ECS cluster?
See: [AWS Docs](https://docs.aws.amazon.com/AmazonECS/latest/userguide/efs-volumes.html), recommends mounting  [[EFS]] file systems onto ECS containers. Tasks running in any AZ will share the same data. Warning: S3 cannot be mounted as a file system.
![[EFS mounted on Fargate and EC2 Architecture.png | 300]]
Fig. EFS can be mounted across a variety of workloads
#UseCase persistent multi-AZ shared storage for your containers. 
Answer: Use [[EFS]].

---

#Q How does EC2 Tasks and Fargate Tasks share Data Volumes between container instances?
See: [Bind Mounts](https://docs.aws.amazon.com/AmazonECS/latest/userguide/using_data_volumes.html) are instance storage on EC2 or ephemeral storage up to 200 GiB.
![[ECS Bind Mounts.png ]]
Fig. Bind Mounts
Answer: Use Bind Mounts for Sidecar pattern.

---
#Q How can an object stored in [[S3]] trigger a task in ECS?
See: S3 can trigger an event into [[EventBridge]] which in turn can start a task in ECS. This results in an end-to-end serverless architecture : object uploaded to S3. S3 sends events to Event Bridge. Event Bridge runs ECS Task. 

---
#Q How can an ECS Task be started on a schedule?
See: Amazon [[EventBridge]] has a timer that can trigger a task.
Answer; Use EventBridge to schedule ECS tasks.

---
#Q How can ECS Tasks handle messages?
See: Tasks can poll [[SQS]] queues.
Answer: ECS Tasks can poll queues, and auto scale based on queue depth.

---

### QUIZ
#Q Which of the following sets of services are used in a typical AWS container stack?
(a) ECR, ECS, EC2
(b) ECS, EMR, EC2
(c) Fargate, ECS, S3
(d) ECR, ECS, S3
Answer: Eliminate S3 because it does nothing for containers. Next, eliminate EMR as it has nothing to do with containers. EC2 can be used as an ECS launch type with the appropriate ECS Agent and Task Role.
### Scaling Services
- AWS Auto Scaling policy  scales out the ECS service when the service’s memory utilization is too high.
- Similarly, when CPU is too high.

#### References for ECS
1. https://aws.amazon.com/ecs/faqs/

---
Created on 2023-03-11 17:54