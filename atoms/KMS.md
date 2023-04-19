### Summary of KMS
Key management system is an #AWSService that automates encryption key management. #secure 

### KMS Details
- [KMS Key Concepts](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html)
- Centrally manage [[Encryption Concepts|encryption]] keys and define policies. Multi-region keys are not supported.
- AWS KMS solution uses an _envelope encryption_ strategy with _AWS KMS keys_. ![[Envelope encryption]]
- Supports Asymmetric and Symmetric keys.
- AWS rotates keys once every year.
- AWS Encryption SDK library should be used from within applications.
- Validate [[Digital Signatures]] and perform signing operations using asymmetric digital keys.
- Message authenticity and integrity with [[HMAC]] (Hash-based Message Authentication Codes)

**KMS Monitoring**
KMS is monitored by [[CloudWatch]] and its usage tracked by [[CloudTrail]]

**KMS Seamless Integration**
>  KMS seamlessly integrates with [[EBS]], [[S3]], [[RDS]], [[SSM Parameter Store]]

#### Types of KMS Keys

|                    | AWS Managed           | Customer Managed |
| ------------------ | --------------------- | ---------------- |
| AWS Generated      | AWS Owned and Managed (annual rotation) | Created in KMS, annual rotation must be enabled.   |
| Customer Generated | Imported to AWS (symmetric only)        | Manual rotation only                |

- The following script will create a base64 encoded file that is encrypted with kms key.
	`aws kms encrypt --key-id alias/mykey --plaintext fileb://SecretFile.txt --output text --query CiphertextBlob --region us-east-1 > SecretFileEncrypted.base64` 
	echo 'SecretFileEncrypted.base64' | base64 --decode > 'SecretFileEncrypted' // this will decode the encrypted file.
to decrypt give a decrypt command with the ciphertext and the blob - it will return a decrypted base64 encoded file back.
`aws kms decrypt --ciphertext-blob fileb://SecretFileEncrypted --output text --query Plaintext ExampleFileDecrypted.base64`


### Cross-Region
Keys created by the service AWS KMS are never transmitted outside of the AWS Region in which they were created. They can be used in only the Region in which they were created.

Plaintext keys are never written to disk and only ever used in volatile memory of the HSMs for the time needed to perform your requested cryptographic operation. This is true regardless of whether you request AWS KMS to create keys on your behalf, import them into the service, or create them in an AWS [[CloudHSM]] cluster using the custom key store feature. Keys created by the service AWS KMS are never transmitted outside of the AWS Region in which they were created. They can be used in only the Region in which they were created.

### Multi-Region KMS Keys

**Multi-Region KMS keys let you encrypt data in one AWS Region and decrypt it in a different AWS Region.**

- Identical KMS keys in different AWS Regions that can be used interchangeably
	- Active-active applications that span multiple Regions
	- DR - Disaster Recovery
	- Global Data Management
	- Global Client Side Encryption
	- Global DynamoDB
	- Global Aurora
	- Distributed signing applications
	- Encrypt in one region and decrypt in another region
- No need to re-encrypt or make cross-Region API calls
- 
  Very select use cases e.g. Global Tables
![[kms_replica_key_cross_region_context.png|512]]
Fig. Keys are managed independently
Architecture for multi-region key replication
![[kms_multi_region_key_context.png|384]]
Fig. Keys are replicated to support global tables

DBA cannot read KMS encrypted columns as they will not have permission to the KMS key. Only an application will be able to decrypt and encrypt.

#### S3 Cross Region Replication with Multi-Region KMS Key
There is currently no benefit to using Multi-Region Key to save time encryption with a multi-region key because they are treated as independent keys by S3. For the same bucket backed up in another region, the objects will be decrypted and then re-encrypted with the same key material in the other region.

### Copy EBS Snapshot Cross Account
#UseCase EBS Snapshot Encryption
An [[EBS]] snapshot in Region A with Key 1 needs to be re-encrypted into Region B with Key 2. Key 1 cannot be used in Region B.
An encrypted snapshot can be moved across accounts (and regions).

**Steps**
1. Attach a KMS Key Policy to authorize cross-account
```
{
	"Sid":"Allow key use to target account/role",
	"Effect":"Allow",
	"Principal":{
	"AWS":"arn:aws:iam:TARGET-ACCOUNT-ID:role/ROLENAME"
	},
	"Action":["kms:Decrypt","kms:CreateGrant"],
	"Resource":"*",
	"Condition":{"StringEquals":{
		"kms:ViaService":"ec2.REGION.amazonaws.com",
		"kms:CallerAccount":"TARGET-ACCOUNT-ID"
	}}
}
```
2. Share the encrypted EBS snapshot across to the [target account](https://aws.amazon.com/blogs/aws/new-cross-account-copying-of-encrypted-ebs-snapshots/).
3. Create a copy of the snapshot, encrypt it with a CMK in the target account.
4. Create a volume from the snapshot.

### Key Policies
- Default Key Policy
	- Created automatically
	- Complete access to the key to the creator of the key policy and account root user = Entire AWS account
	- it does not allow other IAM users or roles to use the key by default
- Custom KMS Key Policy
	- Define users and roles that can access the KMS key.
	- Define who can administer the key.
	- Useful for cross-account access to the key.
- 
---
> **References for KMS**
> 1. https://aws.amazon.com/kms/
> 2. https://aws.amazon.com/kms/features/#AWS_Service_Integration
> 
 
*Created on 2023-03-19 15:26*
