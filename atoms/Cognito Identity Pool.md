- Provide **temporary** AWS Credentials to users so they can access AWS services like S3, Lambda or DynamoDB directly.
- To enable users in your user pool to access AWS resources, you can configure an identity pool to exchange user pool tokens for AWS credentials.
- Unauthenticated guest access supported. It creates two roles - one for authenticated users and one for unauthenticated.
- Federated User Identity, authenticated and unauthenticated users

![[Cognito Identity Pool Token-Cred Swap Architecture.png|512]]
Fig. Cognito CUP CIP Architecture
![[Cognito CIP Architecture Social IdP.png]]
Fig. Cognito CIP Architecture with Social IdP

#Q How is temporary access granted at the row level in [[DynamoDB]]  ?
**Answer**: A policy can be defined for temporary access to mobile or web users to limit the access to AWS resources e.g. DynamoDB row level 
![[Cognito User Identity IAM for DynamoDB.png|512]]
Fig. Support for Row Level security for DynamoDB