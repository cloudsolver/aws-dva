AWS offers several serverless technologies that enable serverless architectures. Serverless is when you don't have to think about infrastructure.

[[Lambda]], [[API Gateway]], [[S3]], [[IAM]],[[DynamoDB]],[[Kinesis]],[[Cognito]],[[Aurora]], [[SNS]],[[SQS]], [[Fargate]], [[CloudFront]]

>Design a ToDo Mobile and Web Application that has a high read and low write needs and requires users to directly upload files to their own S3 buckets with STS.
![[mobile-sts-api-cognito-solution.png]]
Fig. Serverless Architecture

>Blog Site low writes, high reads,  global distribution, dynamic REST API, welcome email to new readers, all images uploaded are thumbnails, low latency and high performance through caching 
Add OAC: Origin Access Control to protect direct access to S3.
![[oac-cloud-front-api-gateway-solution.png]]
Thumbnail generation workflow:
![[edge-cloudfront-oai-oac-apig-solution.png]]
No Cognito needed because it is a public site with no authentication or authorization requirements.

