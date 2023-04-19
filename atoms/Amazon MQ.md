### Summary of Amazon MQ
AmazonMQ is a managed message broker service for RabbitMQ and ActiveMQ. Useful for migration of messaging applications on-prem. #AWSService  
### Amazon MQ Details
- High Availability: Active, Standby - EFS is a backend storage for MQ Broker. Standby is also mounted on the same storage.
![](Amazon%20MQ%20Active%20Passive%20Backed%20by%20EFS.png)

- Amazon MQ is similar to SQS but is used for existing applications that are being migrated into AWS. SQS should be used for new applications being created in the cloud.
- 
#### References for Amazon MQ
1. https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/welcome.html

---
Created on 2023-03-11 00:04