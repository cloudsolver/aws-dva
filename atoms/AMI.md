## Summary
Amazon Machine Image is a regional image that instantiates an [[EC2]] instance.

## AMI Details
Amazon Machine Image are a customization of EC2 instance.
- Add your own software, config, OS, monitoring...
- #UseCase pre-configured, faster initialization.
- AMI are build for specific [region](Region.md). #tip You can copy AMI across Regions.

### Usecases
#UseCase for creating an AMI
1. Start an [[EC2]] instance
2. customize it, 
3. stop the instance, 
4. build an AMI - 
5. this will create [[EBS]] snapshots
6. Launch instance.

![AMI Lifecycle](https://docs.aws.amazon.com/images/AWSEC2/latest/UserGuide/images/ami_lifecycle.png)

#UseCase  for sharing AMI encrypted via KMS*
1. Source Account uses [[KMS]] for [[Encryption Concepts]] of the AMI in the same region.
2. Source Account updates Launch Permission for the Target Account
3. Source Account gives permissions to use KMS key to target account
4. Target Account can decrypt the AMI and launch an instance. 
![[kms_cross_account_key.png]]
Fig. AMI sharing across Accounts

### Quiz 
- #Q You can use an AMI in N.Virginia [Region](Region.md) us-east-1 to launch an [[EC2]] instance in any AWS [[Region]]. True or False? 
- Answer is false.


**References**

1.https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html