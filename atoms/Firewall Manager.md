### Summary of Firewall Manager
Centrally configure and manage firewall rules across accounts and applications. Useful for multi-account [[Organizations]] to enable common security policy. #AWSService 

### Firewall Manager Details

- Security Policy entails
	- [[WAF]] rules for[[ALB]], [[API Gateway]], [[CloudFront]]
	- [[Shield]] to protect [[ALB]], [[NLB]], [[CloudFront]] and [[Elastic IP]]
	- Security Groups for [[EC2]], [[ALB]], [[ENI]] resources in [[VPC]]
	- Amazon Network Firewall
	- [[Route 53]] resolver DNS firewall
- Rules are applied to new resources automatically as well as new accounts that are added to the organization.
- To begin, an administrator account must be set.

---
**References for Firewall Manager**
> 1. https://aws.amazon.com/firewall-manager/faqs/
> 
 
*Created on 2023-03-20 12:55*