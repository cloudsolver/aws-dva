### Summary of ECS
Elastic Container Service requires you to provision and maintain the EC2 instance. #AWSService 

### ECS Details

**EC2 Launch Type**
- Each EC2 instance must run the ECS Agent to register in the ECS Cluster so AWS can start top containers.
- IAM Roles for ECS: ECS Agent. Makes API calls to ECS services, sends container logs to CloudWatch, pull Docker image from ECR, reference sensitive data in Secrets Manager or [[SSM Parameter Store]] Parameter Store. **ECS Task Role** allows each task to have a specific role.
 **Fargate Launch Type**
No need to provision the infrastructure
Create Task definitions, assign memory and CPU.
To scale, just increase the number of tasks.

 [[ELB]] Supported
[[ALB]] supported and works for most use-cases. [[NLB]] recommended for high throughput / high performance use-cases or to pair it with AWS [[PrivateLink]] 
> Data Volume with [[EFS]]
	Mount EFS file systems onto ECS. Tasks running in any AZ will share the same data. S3 cannot be mounted.
![[EFS mounted on Fargate and EC2 Architecture.png | 300]]
Fig. EFS can be mounted across a variety of workloads
	#UseCase persistent multi-AZ shared storage for your containers. 

ECS Deployment Configuration Application Type
 - `Service` to launch a group of tasks handling a long-running computing work e.g. web application
 - `Task` launch a standalone task that runs and terminates e.g. batch job.
> ECS Service Auto Scaling
	AWS Application Auto Scaling (Fargate)
		ECS Service Average CPU Utilization
		ECS Service Average Memory Utilization
		ALB Request Count Per Target
		ECS Service **[[Auto Scaling]]** (Task Level ) is NOT EC2 Auto Scaling (Auto Scaling Group)
	EC2 Launch Type Auto Scaling
		Auto Scaling Group Scaling - 
		**ECS Cluster Capacity Provider** - automatically provision and scale infrastructure.

> ECS Task Invoked by Event Bridge
	-   A serverless architecture : object uploaded to S3. S3 sends events to Event Bridge. Event Bridge runs ECS Task.
	- Amazon Event Bridge can have a timer, that gets triggered. The trigger can start a task.

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