Cloud Development Kit is an open-source software development framework to define cloud infrastructure in code and provision it through AWS [[CloudFormation]].


#Q What are Constructs?
Answer: A component that encapsulates everything that CDK needs to create the final CloudFormation stack. There are 3 layer L1, L2, and L3. L1=Cfn constructs that are available in CloudFormation directly e.g. CfnBucket. L2 has objects you can customize in the CDK e.g. bucket versioning etc. L3 are called patterns - this can abstract common constructs e.g. apigateway backed by lambda `aws-apigateway.LambdaRestApi` .

#Q Where can Constructs be found?
AWS Construct Library is a collection of constructs included in the library. Construct Hub includes additional constructs from 3rd parties including open source CDK.

#Q What are the common CDK commands?
![[CDK-Commands.png]]
Before you can use CDK , it must be bootstrapped CDKToolkit that contains S3, IAM Roles `cdk boostrap aws://<aws_account>/<aws_region>`

#Q How do you test CDK?
Answer; By using CDK Assertions Module. Fine-grained assertions e.g. topics, lambda. Snapshot tests - compare with a baseline CF template.

#Q How can you import a template?
Answer:  `Template.fromStack(MyStack)` <= stack built in CDK. `Template.fromString(mystring)` <= stack built outside CDK.