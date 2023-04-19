### Summary of Inspector
Amazon Inspector is an automated vulnerability management service that continually scans Amazon Elastic Compute Cloud [[EC2]], AWS [[Lambda]] functions, and container workloads like [[ECR]] for software vulnerabilities and unintended network exposure. #AWSService 
### Inspector Details
- Leverages the [[SSM]] aka System Manager for [[EC2]] vulnerabilities.
- Container images when pushed to [[ECR]] will be assessed by Inspector
- [[Lambda]] functions and it's packaged dependencies are inspected for known vulnerabilities and reported.
- AWS [[Security Hub]] and [[EventBridge]] will be notified from there actions can be taken.
- Utilizes vulnerabilities in the known vulnerabilities database: [[CVE]] 
---
> **References for Inspector**
> 1. https://aws.amazon.com/inspector/faqs/?nc=sn&loc=6
> 
 
*Created on 2023-03-20 13:58*