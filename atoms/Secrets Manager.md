### Summary of Secrets Manager
Centrally manage the lifecycle of secrets. #AWSService Primarily for RDS and API keys, DR and secrets compliance. Service offer compares to [[SSM Parameter Store]] with advanced parameters. #secure 

### Secrets Manager Details
- Force rotation of secrets every X days to support compliance 
- Automate generation of secrets of rotation *lambda*
- Integration with Amazon [[RDS]] #UseCase 
- Encryption with [[KMS]]
- Replicate secrets across regions to support [[DR]] #UseCase 
- Read replica secret can be promoted to a standalone secret
- Deleting a Secret causes a 30 day wait period to allow time for cancelling the deletion if required. 

![[Credentials for Services.png|512]]
Fig. Options for Secrets Manager

#Q How does [[CloudFormation]] leverage Secrets Manager?
See:
Answer: `ManageMasterUserPassword: true` - creates a password in SecretsManager and can output an `Arn`. 
![[SecretsManager CloudFormation.png]]
Fig. CloudFormation 
#Q How are multi-region keys supported for DR of Databases ?
See:
Answer: Read-replicas in another region are created and can be promoted in [[DR]] situations.
![[SecretsManager Cross Region Replica.png]]
Fig. Secrets Manager cross region.

---
> **References for Secrets Manager**
> 1. https://aws.amazon.com/secrets-manager/faqs/ 
> 
 
*Created on 2023-03-20 09:30*