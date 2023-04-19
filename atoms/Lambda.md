### Summary of Lambda
AWS Lambda is a serverless, event-driven compute service that lets you run code for virtually any type of application or backend service without provisioning or managing servers. You can trigger Lambda from over 200 AWS services and software as a service (SaaS) applications, and only pay for what you use. #AWSService 
### Lambda Details
- Custom Runtime is  supported e.g. Rust.
- Init times are usually around 100 ms.
- Use [[Step Functions]] to orchestrate workflows.
**Lambda Limits**
- 128 MB - 10 GB max memory, 
- 15 min max timeout,
- 4 KB memory for env variables per function, 
- 50 MB zipped upload deployment package 250 MB unzipped - use /tmp at runtime for additional space,  a better architecture will utilize Lambda layers that helps in reduction of uploads
- 5 max function layers,
- 1000 max concurrency quota
- Lambda is launched outside of VPC by default - so it can access DynamoDB but nothing in a private VPC
* Lamda supports resource-based policies.
**Lambda in [[VPC]]**
- Specify VPC ID, [[Subnet]] and Security Groups.
- AWS will launch Lambda by creating an [[ENI]] assigning IP address (note: scaling requires sufficient IP addresses in the [[subnet]]), Lambda is subject to the same networking rules. 
- Lambda execution requires the following roles `ec2:CreateNetworkInterface`, `ec2:DescribeNetworkInterfaces`  and `ec2:DeleteNetworkInterface` 
- If Lambda requires Internet access - it will need a NAT Gateway.
- Direct connection of lambda to RDS is risky. [[RDS#RDS Proxy]] is recommended for use with Lambda Functions to protect against bottlenecks to avoid too many connections to the database.  #BestPractice 

**RDS and Aurora Invoke Lambda**
- RDS PostgreSQL can invoke Lambda.
- PostgreSQL needs the `aws_lambda` extension installed, IAM roles, networking and other config is needed.
#UseCase Business events can be triggered from the database directly e.g. new role in user table.

**RDS Event Notifications Invoke Lambda**
- These notifications are DB instance lifecycle events as opposed to business events. #UseCase 

### Lambda@Edge
[[CloudFront#CloudFront Functions]]] and lambda@edge can be used for various scenarios and use-cases - see [[Edge Computing Services]].
#UseCase Dynamic web-applications at edge. intelligent routing between origins and data centers. Bot mitigation at the edge. [[A-B Testing Blue-Green Deployment | A/B Testing]] , user tracking, prioritization and analysis.
To use Lambda@Edge, you just upload your code to AWS Lambda and associate a function version to be triggered in response to Amazon CloudFront requests.


**References for Lambda**
1. https://aws.amazon.com/lambda/faqs/
2. https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/PostgreSQL-Lambda.html

---
Created on 2023-03-13 10:33