### Summary of Lambda
AWS Lambda is a serverless, event-driven compute service that lets you run code for virtually any type of application or backend service without provisioning or managing servers. You can trigger Lambda from over 200 AWS services and software as a service (SaaS) applications, and only pay for what you use. #AWSService 
### Lambda Details
- Custom Runtime is  supported e.g. Rust.
- Init times are usually around 100 ms.
- Use [[Step Functions]] to orchestrate workflows.
**Lambda Limits**
- 128 MB - 10 GB max memory. 
- 15 min max timeout.
- 4 KB memory for env variables per function.
- 50 MB zipped upload deployment package 250 MB unzipped - use /tmp at runtime for additional space,  a better architecture will utilize Lambda layers that helps in reduction of uploads.
- 5 max function layers.
- 1000 max concurrency quota.
- Lambda is launched outside of VPC by default - so it can access DynamoDB but nothing in a private VPC.
- Lambda supports resource-based policies.
**Lambda in [[VPC]]**
- Specify VPC ID, [[Subnet]] and Security Groups.
- AWS will launch Lambda by creating an [[ENI]] assigning IP address (note: scaling requires sufficient IP addresses in the [[subnet]]), Lambda is subject to the same networking rules. 
- Lambda execution requires the following roles `ec2:CreateNetworkInterface`, `ec2:DescribeNetworkInterfaces`  and `ec2:DeleteNetworkInterface` 
- If Lambda requires Internet access - it will need a NAT Gateway.
- Direct connection of lambda to RDS is risky. [[RDS#RDS Proxy]] is recommended for use with Lambda Functions to protect against bottlenecks to avoid too many connections to the database.  #BestPractice 

#Q How can Lambda be exposed via HTTP?
See: [DG λ ALB](https://docs.aws.amazon.com/lambda/latest/dg/services-alb.html) and [DG λ Fn URL](https://docs.aws.amazon.com/lambda/latest/dg/lambda-urls.html)
Answer: Either through an [[ALB]] with Target Groups, or via [[API Gateway]]. You must allow the[[ELB]] permissions to invoke Lambda.

#Q How can you ensure that S3 Event Notifications on the same object are sent to Lambda?
*See*: [DG λ S3](https://docs.aws.amazon.com/lambda/latest/dg/with-s3.html)
**Answer**: If Bucket versioning is not setup, it is possible that concurrent updates will result in only one event. Setup versioning on the S3 Bucket.

#Q What problem does Lambda Destination solve?
See: [AWS Compute Blog Post] (https://aws.amazon.com/blogs/compute/introducing-aws-lambda-destinations/)
Answer: For async invocations, it is difficult to know what happened with the execution. Both success and failures can now be sent to a Destination for SQS, SNS, EventBridge, and Lambda as an Execution Record. Limits: Destinations only work with runtimes that are natively supported by Lambda.

#Q How does Lambda process Kinesis Data Streams in a scalable manner?
See: [Blog](https://aws.amazon.com/blogs/compute/new-aws-lambda-scaling-controls-for-kinesis-and-dynamodb-event-sources/)
Answer: Parallelization Factor can be set to 10 (default is 1.). A factor of two allows up to 200 concurrent invocations on 100 Kinesis data shards. It can be changed dynamically. One Lambda function processes one shard at a time. Each parallelized shard must complete before proceeding to the next. On error: blocks processing - entire batch is reprocessed. The shard is paused. The event source mapping can (a) discard old messages, (b) restrict number of retries or (c) split the batch on error.
![[Lambda-Kinesis Batch.png]]
Fig. Lambda Kinesis Batch

#Q How fast does Lambda scale for SQS and SQS FIFO?
Answer: Lambda adds 60 more instances of Firecracker per minute up to 1000 batches concurrently processed.
#Q How are multi-header values supported?
See:
Answer: ALB has a setting to enable it. `?name=Ray&name=Rohit` would become `{'name':['Ray','Rohit']}`

#Q How does Lambda access resources in your VPC?
See:
Answer: Run Lambda inside the VPC. It creates an ENI. Requires `AWSLambdaVPCAccessExecutionRole`. Deploying Lambda inside a public subnet will still not give it Internet access. It will need to be deployed to a private subnet that will route to a NAT device in the public subnet with a route to the IGW.

#Q What can be done to improve initiation time and usage of temporary space.
Answer: Initialize db connections outside the function body.  Use `/tmp` folder for up to 10GB of temporary disk space. Use KMS data keys to encrypt data by yourself.

#Q How does Lambda handle scale concurrency?
See: ![[lambda-reserved-concurrency.png]]
**Answer:** Up to 1000 concurrent invocations (Soft limit) for ALL FUNCTIONS in the account. Be careful with multiple channels saturating concurrency disproportionately. A **reserved concurrency** can be set by the function level. Throttle Error 429 `Rate Exceeded`. For async, DLQ after retry via it's internal event queue. FYI - `provisioned concurrency` is used to ensure lambda functions are ready to scale without fluctionations.

#Q How can the impact of Cold Starts be minimized?
Answer: AWS has improved Lambdas within VPCs. Provisioned Concurrency creates a warm pool can be set that will improve (not free).

#Q How should external dependencies be deployed to Lambda?
Answer: You can zip 50MB with the lambda package. If it's larger, S3 can be used and references via Lambda. Also, Layers helps with reusable libraries to be shared across functions.

#Q What must be done to ensure Lambda Container images?
**Answer**: You must use a base image that implements Lambda Runtime API in [[ECR]]. `FROM amazon/aws-lambda-nodes:12`

#Q What are the best practices for Lambda Container images?
**Answer**: Use AWS provided base images, use multi-stage builds, build from stable to frequently changing, use a single repo for function with large layers. Use these for large lambda functions (up to 10 GB).

#Q What are lambda aliases and how do they relate to lambda versions?
Answer: Aliases are mutable as they point to immutable lambda versions e.g. "dev" alias may point to version "5". Aliases cannot reference aliases. **Weights** can be assigned e.g. 50% version1 and 50% version 2 behind an Alias that can support canary deployments.

#Q How does [[CodeDeploy]] support traffic shift with Lambda?
Answer: Feature is integrated into Lambda. (a) All At Once (b) Canary `10Percent5Minutes`, `10Percent30Minutes` then 100% (c) `Linear10PercentEvery3Minutes`, `Linear10PercentEvery10Minutes` until 100%. Rollbacks can check for pre and post hooks, and if the health is bad, it will be shifted back to the previous version.

#Q How can Lambda be exposed via HTTP/S without ALB or API Gateway?
**Answer**: Lambda Functions: `https://<url-id>.lambda-url.<region>.on.aws` (Dual Stack). No support for PrivateLink only Public Internet. Supports CORS configurations. Throttle via Reserved Concurrency. 

#Q How are Lambda Function URLs secured?
Answer: Both Resource-based and Identity based policies for cross-account. E.g. IAM Role principal from 1st account needs ALLOW for function in 2nd Account. Lambda resource based policy in 2nd account must allow Role from from 1st account to `InvokeFunctionURL`. Within the same account - no need for identity base policy on role.

**RDS and Aurora Invoke Lambda**
- RDS PostgreSQL can invoke Lambda.
- PostgreSQL needs the `aws_lambda` extension installed, IAM roles, networking and other config is needed.
#UseCase Business events can be triggered from the database directly e.g. new role in user table.

#Q How can you execute Lambda function upon RDS DB lifecycle events?
See: [Docs](https://docs.aws.amazon.com/lambda/latest/dg/services-rds.html)
**Answer**: [[RDS]] Event Notifications Invoke Lambda via [[SNS]]. These notifications are DB instance lifecycle events as opposed to business events. SNS does not require Event Source mappings (unique).

### Lambda@Edge
[[CloudFront#CloudFront Functions]]] and lambda@edge can be used for various scenarios and use-cases - see [[Edge Computing Services]].
#UseCase Dynamic web-applications at edge. intelligent routing between origins and data centers. Bot mitigation at the edge. [[A-B Testing Blue-Green Deployment | A/B Testing]] , user tracking, prioritization and analysis.
To use Lambda@Edge, you just upload your code to AWS Lambda and associate a function version to be triggered in response to Amazon CloudFront requests.


**References for Lambda**
1. https://aws.amazon.com/lambda/faqs/
2. https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/PostgreSQL-Lambda.html

---
Created on 2023-03-13 10:33