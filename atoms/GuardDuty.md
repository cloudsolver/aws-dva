
### Summary of GuardDuty
Intelligent Threat detection service fully managed and automated. *GuardDuty analyzes tens of billions of events across multiple AWS data sources, such as AWS CloudTrail events, Amazon VPC Flow Logs, and DNS logs.* #AWSService 
### GuardDuty Details
- Uses [[ML]] to detect anomalies
- [[CloudTrail]] event logs - unusual API calls, unauthorized deployments
- [[VPC]] Flow Logs - unusual internal traffic, IP address
- [[DNS]] logs - compromised EC2 instances sending encoded data within DNS queries
- [[Kubernetes]] audit logs - suspicious activities and potential EKS cluster compromises
- [[EventBridge]] integration for rules.
- CryptoCurrency attacks can be detected out-of-the-box.
![guard|768](https://d1.awsstatic.com/asses-2023/product-rds.5a9aba06b0a59417010ca652cec78591850548be.png)

---
> **References for GuardDuty**
> 1. https://aws.amazon.com/guardduty/faqs/
> 
 
*Created on 2023-03-20 13:52*