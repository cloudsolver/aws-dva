#Q What does CodePipeline integrate with?
See: [Features](https://aws.amazon.com/codepipeline/features/?nc=sn&loc=2)
**Answer**: 
	Source code: [[ECR]], GitHub, [[S3]]. 
	Code Review: [[CodeGuru]]
	Dependencies: [[CodeArtifact]].
	Deploy: [[CodeDeploy]], [[Fargate]], [[EC2]], [[EB | Elastic Beanstalk]]. 
	Build: [[CodeBuild]], Jenkins, CloudBees, TeamCity. 
	Test: AWS Device Farm, [[CodeBuild]]. 
	Deploy: [[CodeDeploy]], [[EB]], [[CloudFormation]]

#Q What is the workflow composed of?
See: [FAQ](https://aws.amazon.com/codepipeline/faqs/?nc=sn&loc=5)
**Answer**: Pipeline, Stages, Transitions, Artifacts and Actions. Example: Build=>Test=>Deploy=>Load Testing. Each stage can have sequential or parallel actions and action groups. Manual approval can be defined at any stage e.g. Deploy Prod.
![|128](https://d1.awsstatic.com/product-marketing/CodePipeline/CodePipeline_Elements.1390531beabe7fd38b2414c39800136eed24e9c8.png)

#Q How should troubleshooting be done?
See:
Answer: Use [[CloudWatch]]Events and [[EventBridge]] e.g. create events for failed pipelines, cancelled stages. Check console for reason. Also check IAM Service Role permissions. Denied API calls can be checked with [[CloudTrail]]

#Q What is the preferred way to trigger CodePipeline?
See: [Migration to Event Driven](https://docs.aws.amazon.com/codepipeline/latest/userguide/update-change-detection.html)
Answer: Use [[EventBridge]] for [[CodeCommit]] and [[CodeStar]] for GitHub. In the past, Web hooks and polling was used.
![[CodePipeline Triggers.png|384]]
Fig. Events

#Q What is the ownership and authorization for Manual Approvals?
See:
Answer: Owner is AWS and Action is 'manual'. IAM permission to GetPipeline and 'PutApprovalResult' is required.

![[CodePipeline Manual Approval Security.png]]