AWS Best Practices for Distributed Denial of Service Attack Architecture


![[osi_model_table.png]]
Fig. Attach Vectors OSI
### Best Practices
![[security_architecture_best_practice_context.png]]
Fig. Best Practices Label

| Defense                                         | AWS Service                                 | Description                                                                                                              |
| ----------------------------------------------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| SYN Flood, UDP Reflection                       | [[CloudFront]]                              | Web Application Delivery at the edge                                                                                     |
| Same                                            | [[Global Accelerator]]                      | Access your application from the edge, without CloudFront                                                                |
| DNS                                             | [[Route 53]]                                | DNS resolution at the edge                                                                                               |
| Infrastructure layer defense                    | [[ELB]], CloudFront, Global Accelerator     | Protect EC2 against high traffice                                                                                        |
| Scale instance on demand                        | [[Auto Scaling]]                            | Scale to protect against bursts                                                                                          |
| Distribute traffic on demand                    | [[ELB]]                                     | Distribute across instances                                                                                              |
| Detect and filter malicious traffic             | [[CloudFront]], [[WAF]]                     | Block geographies with CloudFront, WAF on top of it to block based on request signatures, IP reputation and anonymous IP |
| Mitigate layer 7 attacks                        | [[Shield]]                                  | Protects Route 53, CloudFront, and WAF                                                                                   |
| Obfuscate AWS resources                         | [[CloudFront]], [[API Gateway]] and [[ELB]] | Attacker cannot know what is running the compute workloads EC2 or Lambda                                                 |
| Filter traffic based on IP and ENI-level [[subnet]] | [[NACL]], [[Security Groups]]               | Protect attacks to the [[subnet]] and EC2 instances                                                                          |
|                                                 |                                             |                                                                                                                          |

Being at the edge protects from DDOS, NACL, Security Groups protects our VPC resources. API, ELB obfuscate. WAF can filter anonymous and bad reputation IPs and other problems. API Gateway as well as WAF can protect bursts and rate limiting.

**References**
1. https://docs.aws.amazon.com/whitepapers/latest/aws-best-practices-ddos-resiliency/introduction-denial-of-service-attacks.html
2. 