### Summary of Organizations
Organizations includes account management and consolidated billing capabilities that enable you to better meet the budgetary, security, and compliance needs of your business. #AWSService 
### Organizations Details

> **Advantages**
> Better isolation from multiple accounts than multiple VPCs in a single account. #secure 
> Enable CloudTrail on all accounts
> Establish cross account roles
> Enable CloudWatch logs centrally
> Enable multi-region multi-account Config

> **Root**
> The parent container for all the accounts for your organization. If you apply a policy to the root, it applies to all [organizational units (OUs)](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html#organizationalunit) and [accounts](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html#account) in the organization.
> There is only one root ou which is created by Organizations.

> **OU**
> A container for [accounts](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html#account) within a [root](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html#root). 
> An OU also can contain other OUs, enabling you to create a hierarchy.
>  When you attach a policy to one of the nodes in the hierarchy, it flows down and affects all the branches (OUs) and leaves (accounts) beneath it. 
>  An OU can have exactly one parent, and currently each account can be a member of exactly one OU.

> **Service Control Policies (SCP)**
> 	**Does not apply to Management Account**
> 	IAM policies applied to OU or Accounts to restrict Users or Groups
> 	Just like IAM they don't permit anything - it must have an **explicit allow**

> **Organization Architectures**
> ![[organizations.png|512]]
> Root contains the Management Account. You can't change an organization's management account. Account A will respect parent's deny regardless of it's assign SCP allow list.
> ![Orgs|768](https://docs.aws.amazon.com/images/organizations/latest/userguide/images/AccountOuDiagram.png)
> OU can be part of a hierarchy with a simple 1:1 carnality between parent and child.

**S3 Bucket Policy Restricted to Organization**

```
{   
	"Version": "2012-10-17",   
	"Statement": [     
		{       
			"Sid": "AllowBucketAccess",       
			"Effect": "Allow",       
			"Action": [         
				"s3:GetObject",         
				"s3:PutObject"       
				],       
			"Resource": "arn:aws:s3:::my-bucket/*",
			"Condition": {         
				"StringEquals": {           
					"aws:PrincipalOrgID": "o-1234567890"         
				}       
			}     
		}   
	] 
}
```
---
> **References for Organizations**
	1. Concepts https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html
 
*Created on 2023-03-16 20:34*