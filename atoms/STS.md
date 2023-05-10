#Q What is STS?
Secure Tokenization Service that enables limited privilege, temporary credentials for users to access Amazon services. #AWSService 

#Q What are main services that utilize STS?
- [[Cognito]] utilizes STS
- STS supports AWS [[CloudTrail]] to log all access.
- [[AWS CLI]] v2 utilizes STS.

#Q How do you allow an external contractor to perform some tasks on your AWS account?
See: [Blog](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_cross-account-with-roles.html)
Answer: Provide them a cross-account access and assign role.

#Q What are the STS APIs ?

Answer: `AssumeRole`, `AssumeRoleWithWebIdentity`, `AssumeRoleWithSAML`, `GetSessionToken` for MFA, `GetFederatedToken`, `GetCallerIdentity` and `DecodeAuthorizationMessage`

#Q What are timing constraints of the token validity?
Answer: The tokens can set to expire between 15(min)-60(max) mins.

#Q How is STS with MFA used?
Answer: GetSessionToken returns AccessID, SecretKey and SessionToken. `MultiFactorAuthPresent:true` must be a Condition in the IAM permissions.

 **References for STS**
1. https://docs.aws.amazon.com/STS/latest/APIReference/welcome.html

---
Created on 2023-03-13 18:40