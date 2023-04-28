**EC2 Launch Type**
- Each EC2 instance must run the ECS Agent to register in the ECS Cluster so AWS can start top containers.
- IAM Roles for ECS: ECS Agent. Makes API calls to ECS services, sends container logs to CloudWatch, pull Docker image from ECR, reference sensitive data in Secrets Manager or [[SSM Parameter Store]] Parameter Store. **ECS Task Role** allows each task to have a specific role.

---

#Q What are the Task Placement Types and Constraints that can be applied when launching an EC2 Launch Type?
See: [Task Placement Strategy](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-placement-strategies.html).
Task Placement Strategy is a best effort (not guaranteed)
![[ECS Spread Placement Strategy.png]]
Fig. ECS Cluster Placement Strategy
**Answer**. It is an algorithm for selecting instances (a) binpack, (b) random and (c) spread (default).

---

#Q How are Task Placement Constraints used in ECS?
See: [Task Placement Constraints](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-placement-constraints.html) are of two types `distinceInstance` and `memberOf`.  Instance id, type, vpc, subnet, os etc can be used as constraints.
**Answer**: A _task placement constraint_ is a rule that's considered during task placement.

---


