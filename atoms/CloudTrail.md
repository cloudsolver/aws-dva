### Summary of CloudTrail
Governance, audit and compliance for your organization. #AWSService 
### CloudTrail Details
- CloudTrail records API calls made from any client. The AWS Management Console, AWS Software Development Kits (SDKs), command line tools, and higher-level AWS services call AWS API operations, so these calls are recorded.
- Per Region limit of 5 trails. 
- Each trail is 90 days retention by default. For longer retention move them to [[S3]] and use [[Athena]].
- CloudTrail default settings **encrypt** the logs.
- Works with [[Config]] and [[CloudWatch]]
- #UseCase if any resource is deleted, always start the investigation with CloudTrail.
- #UseCase Ensure log files are not tampered. Enable `Log file validation`

| Event Type                     | UseCase                                                                                       |
| ------------------------------ | --------------------------------------------------------------------------------------------- |
| Management Events (default on) | Operations on AWS resources e.g. `IAMAttachRolePolicy` can separate Read versus Write events. |
| Data Events (default off)      | S3 operations, Lambda operations etc. This is high volume.                                    |
| Insight                        | Creates a baseline and then alerts on anomalies e.g. gaps in periodic maintenance, bursts, service limits. ![[cloudtrail-insights-insight-event-generation-context.png]]                                                                                              |

*Note*: In order to log access to S3 bucket access. Data Events will need to be turned on.

> **Notification Solution Architecture on table deletion with CloudTrail**
> ![[CloudTrail tracks DELETETABLE API call.png|512]] 
> Fig. DynamoDB table deletion sends an email via [[EventBridge]]
> EventBridge gets events automatically. 

**Unmodifiable organization-wide trail Solution Architecture**
You can create a CloudTrail trail in the management account with the **organization trails** option enabled and this will create the trail in all AWS accounts within the organization.
Member accounts can see the organization trail but can't modify or delete it. By default, member accounts don't have access to the log files for the organization trail in the Amazon S3 bucket.

---
> References for CloudTrail
1. https://aws.amazon.com/cloudtrail/faqs/ 

*Created on 2023-03-15 23:03*