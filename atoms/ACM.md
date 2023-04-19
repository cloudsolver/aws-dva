### Summary of ACM
AWS Certificate Manager is an AWS service for creating certificates. #AWSService
### ACM Details
- TLS Certificates on [[ALB]] are enabled with ACM to provision HTTPS for in-flight [[Encryption Concepts]] - you can redirect HTTP to HTTPS #secure 
- Free for public TLS certificates; automatic TLS certificate renewal 60 days prior to expiration.
- ACM creates a managed AWS KMS key with the alias `aws/acm`. ACM uses this [[KMS]] key to encrypt the certificate's private key.
- FQDN are validated via DNS CNAME entry or email from the WHOIS database.
- Integrates with [[NLB]], [[CloudFront]], [[API Gateway]] etc
- **All [[CloudFront]] certificates are in us-east-1 region.**
- For API Gateway (Edge Optimized) - the ACM must be in us-east-1. For Regional, ACM must be in the region as the API Stage.
- [[ELB]] uses X.509 certificate that can be managed within ACM.
- You can upload your own certificates.
- ACM sends daily expiration events for imported certificates to [[EventBridge]] - from there you can integrate to [[Lambda]] or [[SNS]] or [[SQS]]

 #Q How can you be notififed before certificates are set to expire?
>Create an Amazon EventBridge (Amazon CloudWatch Events) rule that will check AWS Health or ACM expiration events related to ACM certificates. Send an alert notification to an Amazon Simple Notification Service (Amazon SNS) topic when a certificate is going to expire in 30 days.

![[EventBridge Rules Notification.png]]
Fig. EventBridge Notifications
#### Constraints
 - **Certificates in ACM are regional resources**. To use a certificate with Elastic Load Balancing for the same fully qualified domain name (FQDN) or set of FQDNs in more than one AWS region, you must request or import a certificate for each region.
- Cannot use public certificates with [[EC2]] 
---
> **References for ACM**
> 1. https://docs.aws.amazon.com/acm/latest/userguide/data-protection.html
> 
 
*Created on 2023-03-20 11:14*