### Summary of IAM
Identity and Access Management is a core #awsservice  Global Service. #secure 

### IAM Details

 **IAM User**
- Features and Restrictions
	- Users: mapped to a physical user, has a password for AWS Console
	- Many users can be created. 
	 - Principle of least privilege: give users only rights they need to do their job. #WellArchitected
	- Changes to IAM groups are live immediately. Policy can be attached directly, and by groups.

**IAM Group**
 - Features and Restrictions
	- Groups: contains users only. 
	- Groups can't be nested.
	- Groups can be given permissions via IAM Policy.
	- Groups are NOT an identity, and cannot be identified as principals in an IAM policy. But the following is possible:
		- `"Condition":{"StringEquals":{"aws:PrincipalTag/group":"developers"}}`


**IAM Policy**
- An IAM Policy is a JSON document that outlines permissions for users or groups.
	* Users or Groups can be assigned JSON documents called Policies.
	* Policies declare permissions. You can inherit policies, but not roles.
	* IAM Policy contains 'version'
	* IAM Policy Statement contains Sid, Effect, Principal, Action, Resources, and Condition.
	* `sid` is the statement identifier that describes the policy statement.
	
  
**IAM Role**
- IAM roles are a way to grant temporary permissions to users, applications or services without the need to share long-term access keys or credentials.
- IAM Roles for [[EC2]] instance or AWS Services.
	* IAM Role for Services:
	* Perform actions on your behalf 
	* Assign permissions to AWS services with IAM Roles e.g. [EC2](EC2.md) Instance, Lambda, etc.
* Security: MFA + Password policy.
	* IAM password policies can be protected by requiring complexity: min length, specific character types, numbers, non-alphanumeric characters, expiration, prevent reuse and change password by user.
	* Password policies are done at the account level (not IAM policy)
	* MFA: protect Root and IAM users. Password you know + Security device you own.
	* Users can assume IAM role while accessing resources from the production environment
* Access Keys: CLI or SDK
* [[Audit]]: [[CredentialsReport]] and [[Access Advisor]] 

**IAM Conditions**
Various IAM conditions can be applied via policies e.g. `aws:sourceIp` , `aws:RequestedRegion`, `ec2:ResourceTag`, etc.
![[clientIP IAM policy.png|384]]
Fig. Deny all IPs unless the request comes from the listed IPs.

![[tag attribute permissions.png|384]]
Fig. Resource Tag / Project "DataAnalytics"

**Permission Boundaries**
Does not apply to Groups. *Supports Users and Roles only.*
AWS supports _permissions boundaries_ for IAM entities (users or roles). A permissions boundary is an advanced feature for using a managed policy to set the maximum permissions that an identity-based policy can grant to an IAM entity. An entity's permissions boundary allows it to perform only the actions that are allowed by both its identity-based policies and its permissions boundaries.
*Does not apply to groups.*
![[iam-scp-permissions_boundary.png|384]]
Fig. Boundaries
**IAM Roles compared to Resource-Based Policies**
![[IAM roles versus Bucket policy.png|384]]
Fig. Both options to access the bucket are valid.

| IAM Roles                                                               | Resource-Based Policies                                                              |
| ----------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| You must give up all your original permissions when you take on a role. | Principal does not have to relinquish permissions.                                   |
| You cannot scan a db and write to a bucket                              | Use principals db permissions to scan and bucket resource-based permissions to write |

EventBridge must use IAM Role when writing to Kinesis.

Evaluation Logic: https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html

#Q A company has over 2000 users and is planning to use S3 bucket/home/%username% folder structure. What steps should be taken so that the users have access to only their folder? (Pick Two)
(a) Create an IAM Policy that applies object-level S3 ACLs
(b) Create a bucket policy that applies access permissions based on username
(c) Create an IAM group and attach the IAM policy
(d) Attach an S3 ACL sub-resources that grants access based on the %username% variable
(e) Create an IAM policy that applies folder level permissions

Answer: The core idea is to differentiate between Role based on Resource based policy. Resource based policies will not scale for 2000 users. IAM will need to be used to grant access to folder level permissions. The other options are tricky. (c) and (e) are the correct options.


**IAM Guidelines & Best Practices #bestpractice**
1. Don't use root.
2. One physical user 
3. Assigned users to groups and assign permissions to groups
4. Strong password
5. MFA
6. Use Roles for permissions to AWS services
7. Use Access Keys for CLI SDK
8. [[CredentialsReport]] for audit.
9. Use [Access Advisor](Access%20Advisor.md) to review policies and least priviledge adjustments. [[Access Advisor]] shows the services permissions granted to the user and when those services were last accessed. You can use this information to review your policies later.
10. AWS documented IAM best practices: [Click Here](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)

#### IAM Identity Center
- SSO for all accounts in the organization and third party applications
- Integrates with 3rd party identity providers

![[Multi-account IAM ID Center Org.png]]
Fig.

- Enable IAM Identity Center and create a two-way forest trust to connect customer's self-managed Microsoft AD with SSO by using AWS Directory Service.
#### Quiz
#Q An IAM policy consists of one or more statements. A statement in an IAM policy consists of the following, EXCEPT:
	1. Effect
	2. Principal
	3. Version
	4. Action
	5. Resource
	Answer: This is a tricky question because the JSON contains everything listed. However, the version is at a higher level than the statement itself.

#Q What happens when a user has restricted policy as well as a group that has permissions that override that restriction?
1. The "explicit deny" principle will hold true. This means that a deny always overrides any allow regardless of where the deny is.

#Q  Which of the following is an IAM Security Tool?
1. [[CredentialsReport]]
2. IAM Root Account Manager
3. IAM Services Report
4. IAM Security Advisor
Answer: This is a tricky question because when the question is framed like a 'tool' you would want to pick IAM Securtiy Advisor thinking it is the IAM [Access Advisor](Access%20Advisor.md). However, that would be incorrect becauser there is no Security Advisor within IAM. There is a report that comes out of IAM i.e. [[CredentialsReport]] - but it is not a tool. Is it? Well, I guess that's the answer for this question.

You can enable IAM **cross-account access** for all corporate IT administrators in each child account.

#### References

1. https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html