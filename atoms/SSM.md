### Summary of Systems Manager
AWS Systems Manager aka SSM is the operations hub for your AWS applications and resources and a secure end-to-end management solution for hybrid cloud, and multi-cloud environments that enables secure operations at scale. #AWSService 
### Systems Manager Details

1. Features [[SSM Parameter Store]] Parameter Store.
2. Features ability to use an agent to log in to an [[EC2]] instance without enabling port 22 for [[SSH]] in [[SG | security group]]
3. Run Command - run scripts on EC2 instances (or on prem nodes). No need for SSH. Runs through agent, command logs are sent to S3 or SNS for status. Integrated with CloudTrail. EventBridge is automated. Run via SSM agent.

![[Run Command Architecture.png|512]]
Fig. Run Command integration from SSM

4. Patch Management - OS, Sec Updates, cross platform. Scheduled on maintenance windows. Compliance reports
![[Run Command Invocation Architecture.png|512]]
Fig. Maintenance Window - batch update for Patch 

5. Automation: Run books are SSM docs that can take action on EC2 instances. e.g. snapshots of EBS. Integrates with [[Config]] - apply remediations that match findings.

### Patch Manager versus Run Command

If you need to automate patching and compliance for your instances, you should use SSM Patch Manager. If you need to execute ad-hoc commands or scripts on your instances, you should use Run Command. #UseCase 

---
**References for Systems Manager**
1. https://aws.amazon.com/systems-manager/ 
 
*Created on 2023-03-20 09:23*