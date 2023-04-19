### Summary of Fargate
Serverless compute engine for containers that works with [[ECS]] and [[EKS]]
### Fargate Details
- Mounting [[FSx]] for Lustre on AWS Fargate is **NOT** supported. All high performance file access must use [[EFS]] or other.
- Choose AWS Fargate for its isolation model and security. You should also select Fargate if you want to launch containers without having to provision or manage EC2 instances. If you require greater control of your EC2 instances or broader customization options, then use ECS or EKS without Fargate. 
- Use EC2 for GPU workloads, which are **NOT** supported on Fargate today.

**References**
1. https://aws.amazon.com/fargate/faqs/?nc=sn&loc=4

---
Created on 2023-03-11 21:13