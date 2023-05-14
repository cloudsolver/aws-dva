### Summary of ECR
Elastic Container Registry is where Docker images are **stored** and managed on AWS. This is integrated with [[Lambda]], [[ECS]], and [[EKS]]. #AWSService 

### ECR Details

#Q What are the benefits of ECR?
See: [Vulnerability Scanning](https://docs.aws.amazon.com/AmazonECR/latest/userguide/image-scanning.html) with integration to [[Inspector]] along with other features such as versioning, image lifecycle and a private and public repo https://gallery.ecr.aws.
**Answer**: Security, management, private and public repos that are fully integrated into ECS.

#Q How do you sign-in to ECR before a `docker pull`?
See:
Answer: `$(aws ecr get-login --no-include-email)`

**References for ECR**
1. https://aws.amazon.com/ecr/faqs/

---
Created on 2023-03-11 21:23