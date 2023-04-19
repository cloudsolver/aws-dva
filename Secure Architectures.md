## Secure

### Design secure access to AWS resources.
**Knowledge**
1. Access controls and management across multiple accounts.
2. AWS federated access and identity services. AWS Identity and Access Management ([[IAM]]), AWS Single-Sign-On with [[IAM Certificate Store]].
3. AWS [[Global Infrastructure]] (AZ, AWS Regions).
4. AWS Security Best Practices (e.g. Principle of Least Privilege).
5. The AWS Shared Responsibility Model.

**Skills**
1. Applying AWS security best practices to [[IAM]] users and root users (for example, multi-factor authentication [[MFA]])
2. Designing a flexible authorization model that includes [[IAM]] users, groups, roles and policies.
3. Designing a security strategy for multiple AWS accounts (for example, AWS [[ControlTower]], Service Control Policies [[SCP]]).
4. Determine the appropriate use of resource policies for AWS services.
5. Determining when to federate a directory service [[AD]] with [[IAM]] roles.

### Design secure workloads and applications.
**Knowledge**
1. Application configuration and credentials security.
2. AWS service endpoints.
3. Control ports, protocols, and network traffic on AWS.
4. Secure application access.
5. Security services with appropriate use cases (for example, Amazon [[Cognito]], Amazon [[GuardDuty]], Amazon [[Macie]]).
6. Threat vectors external to AWS (for example, DDoS, SQL injection)

 **Skills**
1. Designing [[VPC]] architectures with security components (for example, security groups, route tables, [[NACL]], [[NAT]] gateways).
2. Determining network segmentation strategies (for example, using public subnets and private subnets).
3. Integrating AWS services to secure applications (for example, AWS [[Shield]], AWS [[WAF]], AWS [[SSO]], AWS [[Secrets Manager]]).
4. Securing external network connections to and from the AWS Cloud (for example, [[VPN]], AWS [[DX]]).

### Determine appropriate data security controls

**Knowledge**
1. Data access and governance.
2. Data recovery.
3. Data retention and classification.
4. Encryption and appropriate key management.

** Skills**
1. Aligning AWS technologies to meet compliance requirements.
2. Encrypting data at rest (for example, AWS Key Management Service [[KMS]])
3. Encrypting data in transit (for example, AWS Certificate Manager [[ACM]] using [[TLS]])
4. Implementing access policies for encryption keys.
5. Implementing data backups and replications.
6. Implementing policies for data access, life-cycle, and protection.
7. Rotating encryption keys and renewing certificates.