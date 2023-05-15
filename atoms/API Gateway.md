### Summary of API Gateway
Amazon API Gateway is a fully managed service to create, publish, maintain, monitor, and secure  RESTful APIs and WebSocket APIs that enable real-time two-way communication applications. #AWSService  
### API Gateway Details
- Expose any AWS Service via API Gateway.
- Supports containerized and serverless workloads, as well as web applications integrates with [[ELB#ALB]], [[Lambda]]
- #UseCase API Gateway is helpful to add features such as throttling, rate-limiting, caching responses, API Keys etc. to your application.
- API Gateway has a feature that can proxy AWS Service APIs for DynamoDB, Kinesis and CloudWatch as these services have APIs.

#Q How are stage variables passed down to [[Lambda]] functions?
See:
Answer: Stage variables are injected into the `context` object. A stage variable is often used to connect to a lambda alias. The alias can point either all the traffic or partial traffic to a set of lambda functions. This can be done without any changes to the API Gateway. The stage variable name becomes part of the URL.

#Q What does a Canary promotion accomplish?
Answer: It updates the canary prod deployment to production.

#Q How can API Gateway support JSON in the front-end and SOAP in the backend?
Answer. VTL (Velocity Template Language) can be used to modify headers, body and perform changes based on loops etc. The Content-Type must be JSON or XML `Content-Type: application/json`.  Query parameter names can be modified as well.

#Q How does Request Validation behave?
Answer: OpenAPI is supported and it checks for JSON schema, parameters, query strings, and headers. A validation failure returns a 400.

#Q How does Caching work?
Answer: Response are cached with a min-default-max:0-300-3600 seconds. Size: 0.5GB-237GB. Invalidations should be protected with [[IAM]] permissions, otherwise `Cache-Control:max-age=0` will invalidate the cache. This is expensive so best to use in production only. Granularity - method level. 

#Q What are key CloudWatch metrics?
Answer: Metrics are at the stage level. `CacheHitCount` and `CacheMissCount` indicate cache efficiency. `Count` total number of API calls. `IntegratonLatency` the time the backend is taking. `Latency` the total time between a request and a response from the Gateway. Errors: `4xx` are client-side and `5xx` are server side.

#Q API Gateway invocation limits?
Answer: 10000 requests per second at the account level.

#Q How is CORS configured in API Gateway?
Answer: It is at the method level. In case of lambda-proxy - the lambda function must return the header `Access-Control-Allow-Origin: https://www.example.com`. Other headers are Methods, Headers, Max-Age.

#Q What should be done to only allow authorized clients to invalidate an API Gateway cache entry when submitting API requests?
See:
Answer: The client must send the request with a header `Cache-Control: max-age=0`. It it prudent to turn on `Require Authorization` for the API and this can be done by checking the check-box of the Cache Settings.

#Q What are the Integration types supported and when should each be used?
See: [Docs](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-integration-types.html)
Answer: 

| Type       | Desc |
| ---------- | ---- |
| HTTP       | Expose HTTP endpoints in the backend. Known as the HTTP custom integration, you must configure both the integration request and integration response. You must set up necessary data mappings from the method request to the integration request, and from the integration response to the method response.     |
| AWS        |  Expose AWS service actions. Integration layer and Data mapping config required.   |
| HTTP-PROXY | Pass through directly. Method level.     |
| AWS-PROXY  |  Pass through directly to [[Lambda]] ONLY. All other AWS services - must use AWS option.    |
| MOCK           |  No backend is called.    |

Table. Integration Types

Note: Use PROXY if you don't want API Gateway to mess around with integration layers and mappings. 

#### API Gateway Security
-  [[IAM]]
	- Authorize Services with the AWS ecosystem.
	- Leverage Sigv4 for invoking API Gateway
	- Use for Resource Policy for Cross-Account Users, Roles
- [[Cognito]] 
	- Use for Mobile users that already have Cognito User Pool token
	- Pass the connection Token that API Gateway can validate
- [[Lambda]] Custom Authorizers 
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