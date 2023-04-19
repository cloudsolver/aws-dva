### Summary of API Gateway
Amazon API Gateway is a fully managed service to create, publish, maintain, monitor, and secure  RESTful APIs and WebSocket APIs that enable real-time two-way communication applications. #AWSService  
### API Gateway Details
- Expose any AWS Service via API Gateway.
- Supports containerized and serverless workloads, as well as web applications integrates with [[ELB#ALB]], [[Lambda]]
- #UseCase API Gateway is helpful to add features such as throttling, rate-limiting, caching responses, API Keys etc. to your application.
- API Gateway has a feature that can proxy AWS Service APIs for DynamoDB, Kinesis and CloudWatch as these services have APIs.

#### API Gateway Security
-  IAM
	- Authorize Services with the AWS ecosystem
- [[Cognito]] 
	- Use for Mobile users
- Lambda Custom Authorizers 
	- (e.g. JWT verification, OAuth provider callout) that return IAM policies which are used to authorize the request.
- Custom Domain names for API Gateway are possible.
	- IAM roles and policies or AWS Lambda Authorizers to authorize access to your [[WebSocket]] APIs.
- API Keys
	- We do not recommend you use API keys for authorization. #antipattern 
	- You should use API keys to monitor usage by third-party developers and leverage a stronger mechanism for authorization, such as signed API calls or OAuth. #secure 
#### Cache and Throttling
- You enable caching by stage. Not method.
#### Endpoint Types

| Type                         | Description                                                                                                                |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Edge-Optimized (default)** | The API Gateway still lives in one region.Requests are routed via [[CloudFront]] locations to improve latency. #performant |
| **Regional**                 | For clients that are in one region. However, [[CloudFront]] can be used to optimize.                                           |
| **Private**                  | Accessed only from within [[VPC]] using its interface  endpoint [[ENI]]                                                    |



#### References for API Gateway
1. https://aws.amazon.com/api-gateway/faqs/

---
Created on 2023-03-13 15:54