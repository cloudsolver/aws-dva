How does ECS automatically increase or decrease number of Tasks?
By using AWS Application Auto Scaling with [[ASG]]. It monitors:
- ECS Service Average CPU Utilization
- ECS Service Memory Utilization
- [[ALB]] Request Count Per Target

ECS Service Auto Scaling
AWS Application Auto Scaling (Fargate)
ECS Service Average CPU Utilization
ECS Service Average Memory Utilization
ALB Request Count Per Target
ECS Service **Auto Scaling** (Task Level ) is **NOT** the same as EC2 Auto Scaling (Auto Scaling Group)
EC2 Launch Type Auto Scaling
Auto Scaling Group Scaling - 
**ECS Cluster Capacity Provider** - automatically provision and scale infrastructure.

#Q What types of scaling policy can ECS use?
See: [[Autoscaling Policies]]
Answer: ECS uses target, simple and scheduled (not simple).