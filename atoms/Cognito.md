### Summary of Cognito
Fully managed Customer Identity and Access Management that provides user authentication via User Pools and authorization via Identity Pools for web and mobile applications.  #AWSService #secure 
### Cognito Details
- Scale to millions of users with a fully managed, high-performant, and reliable identity store.
- Federate sign-in using [[OIDC]] or [[SAML]] 2.0 and connect to a broad group of AWS services and products.
- Support adaptive [[authentication]], support compliance, and [[data residency]] requirements.
####  User Pools 
- Create and managing a user directory for your application, providing secure user authentication and authorization features out-of-the-box
- [[User directory service]]. Sign-up and sign in to provide authentication for app users.
- Move authentication capability from the backend of your application to Cognito.
- Serverless database for users - supports for MFA, email verification, third party auth e.g. Google auth.
![[User Pool Auth Architecture.png|512]]
Fig. User Auth, [[Tokenization]],  and Integration with [[API Gateway]] and [[ELB#ALB]]
####  Identity Pools
- To enable users in your user pool to access AWS resources, you can configure an identity pool to exchange user pool tokens for AWS credentials.
- Federated User Identity, authenticated and unauthenticated users
- Provide **temporary** AWS Credentials to users so they can access AWS services like S3, Lambda or DynamoDB directly.
![[Cognito Identity Pool Token-Cred Swap Architecture.png|512]]
Fig. Architecture
- A policy can be defined for temporary access to mobile or web users to limit the access to AWS resources e.g. DynamoDB row level 
![[Cognito User Identity IAM for DynamoDB.png|512]]
Fig. Support for Row Level security for DynamoDB
#### References for Cognito
1. https://aws.amazon.com/cognito/dev-resources/

---
Created on 2023-03-13 16:36