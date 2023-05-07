Serverless Application Model is IaC that sits on top of [[CloudFormation]] and targets an easier way to declare AWS Serverless infrastructure.

#Q How does SAM assist development teams?
Answer: SAM can run [[API Gateway]], [[Lambda]] and [[DynamoDB]] locally with SAM CLI and AWS Toolkits. `sam local start api` etc. It can run templates generated with [[CDK]].

#Q How does SAM work?
Answer: SAM will transform to CloudFormation and then it's basically the same. It requires `Resources` and `Transform` sections. `sam build`, `sam package`
 and `sam deploy` commands.
 
 ![[SAM Architecture Flow.png]]

#Q How are policies specified in SAM for your lambda functions?
Answer: Policy templates e.g. `S3ReadPolicy`, `SQLPollerPolicy`, `DynamoDBCrudPolicy`.

#Q How does SAM update Lambda functions?
Answer: It natively uses [[CodeDeploy]].

![[SAM-CodeDeploy.png]]

#Q What is SAR?
Answer: Serverless Application Repository. Build and publish serverless applications that can be used by organizations. Share with AWS accounts or publicly.
