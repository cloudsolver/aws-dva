### Summary of Secrets Manager
Centrally manage the lifecycle of secrets. #AWSService Primarily for RDS and API keys, DR and secrets compliance. Service offer compares to [[SSM Parameter Store]] with advanced parameters. #secure 

### Secrets Manager Details
- Force rotation of secrets every X days to support compliance 
- Automate generation of secrets of rotation *lambda*
- Integration with Amazon [[RDS]] #UseCase 
- Encryption with [[KMS]]
- Replicate secrets across regions to support [[DR]] #UseCase 
- Read replica secret can be promoted to a standalone secret

![[Credentials for Services.png|512]]
Fig. Options for Secrets Manager



---
> **References for Secrets Manager**
> 1. https://aws.amazon.com/secrets-manager/faqs/ 
> 
 
*Created on 2023-03-20 09:30*