### Summary of SSM Parameter Store
Provides secure, hierarchical storage for configuration data management and secrets management. It is a capability of [[SSM]] #secure 
### SSM Details
A centralized way to manage configuration data.
Security through [[IAM]]
Notifications with Amazon [[EventBridge]]
[[CloudFormation]] can use for stacks.
Only supports symmetric keys #
Store data such as 
- passwords, (reference secrets in Secrets Manager)
- database strings, 
- Amazon Machine Image (AMI) IDs, and 
- license codes as parameter values. 
- You can use [[Secrets Manager]] to automatically rotate secrets stored in Parameter Store.
 
You can store values as plain text or encrypted data. You can reference Systems Manager parameters in your scripts, commands, SSM documents, and configuration and automation workflows by using the unique name that you specified when you created the parameter.

SSM Parameter store integrates with AWS [[Secrets Manager]]. Here's how to integrate -  [aws doc](https://docs.aws.amazon.com/systems-manager/latest/userguide/integration-ps-secretsmanager.html).

SSM Parameter store integrates seamlessly with [[KMS]] create secure string parameters. Parameter Store uses AWS KMS keys to encrypt the parameter values of secure string parameters when you create or change them - [aws doc](https://docs.aws.amazon.com/kms/latest/developerguide/services-parameter-store.html)

Practical note: A parameter name cannot end with a forward slash
You can retrieve the entire path with `get-parameters-by-path`
```
aws ssm get-parameters-by-path --path /parking --recursive --with-decryption
```
### Parameter Policies
Advanced parameters supports policies. Once you create an Advanced Parameter - you cannot downgrade it.
#UseCase How do you create a db credential expires in 90 days and a reminder be sent 15 minutes?
Create the credential in the parameter store with multiple policies
```
"Type":"Expiration".
"Attributes":{
	"Timestamp":"2023-12-31T13:00:00.000Z"
}
```
An expiration notification to [[EventBridge]] will be sent by adding the following
```
"Type":"ExpirationNotification",
"Attributes":{
	"Before":"15",
	"Unit":"Days"
}
```


---
> **References for SSM**
> 1. https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html
> 2. https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html
> 
 
*Created on 2023-03-19 20:17*