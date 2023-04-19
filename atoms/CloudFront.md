## Summary
CloudFront is a Content Distribution Network (CDN) Service offered by AWS. #AWSService 
## CloudFront Details
As soon as the first byte arrives from the origin, CloudFront begins to forward the object to the user. CloudFront also adds the object to the cache for the next time someone requests it. While this service is useful for content distribution however for UDP, and non-HTTP acceleration such IoT this won't work. Instead, we must use [Global Accelerator](Global%20Accelerator.md) if business has more advanced use-cases such as requiring whitelisting IP addresses, reduced latency and performance.

![Architecture|384](https://docs.aws.amazon.com/images/AmazonCloudFront/latest/DeveloperGuide/images/how-you-configure-cf.png)
Fig. Conceptual Architecture

Regional Caches are large than POPs and can hold less popular objects. This saves a trip to the origin servers and keeps objects cached closest to the customer.
- Supports 30 GB file size [limits](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cloudfront-limits.html)
- You can enable geo restrictions in CloudFront. #secure 
- You can choose **Price Class 100**, viewers in India might experience higher latency than if you choose **Price Class 200**. #CostOptimized 
- Lambda@Edge with CloudFront enables a variety of ways to customize the content that CloudFront delivers. #UseCase 
- Accelerate static site delivery, VOD, field-level encryption are some of the UseCases.
- CloudFront works with [[WAF]] to filter IPs. CloudFront will terminate the connection and VPC will not see Client IPs - so [[NACL]] is not useful.
- CloudFront can use HTTPS to communicate with an Elastic Load Balancing load balancer, an Amazon EC2 instance, or another custom origin.
- CloudFront supports [[RTMP]] for Video and Audio streaming. A CloudFront distribution is either a Web Distribution or an RTMP distribution but not both.
### CloudFront HA
Set up an Origin Group with Primary and Secondary Origins. #Resilient 
You can set up CloudFront with origin failover for scenarios that require high availability. To get started, you create an _origin group_ with two origins: a primary and a secondary. If the primary origin is unavailable or returns specific HTTP response status codes that indicate a failure, CloudFront automatically switches to the secondary origin.

### CloudFront Functions
- Regional Edge Cache runs within 13 AWS Regions.
![[CloudFront Functions Architecture.png|128]]
Fig. Conceptual Architecture
- Edge Locations are 255 data centers across 47 countries (2022) that run limited AWS Services e.g. S3, AWS Shield, Route 53 etc.
- Files as large as 20 GB can be delivered.
- CloudFront functions are constrained JavaScript functions executed before the request hits the cache. 
![CloudFront Functions Architecture|256](https://miro.medium.com/v2/resize:fit:1400/0*feB6kqJ_WjWbpggD)
- Native feature of CloudFront Functions
- Constraints
	- No access to Internet
	- No use of await async
	- No access to file system
	- The date function returns the same time i.e. time of execution start
	- Size of code is limited to 10 KB
Some of these constraints are lifted when using [[Lambda#Lambda@Edge]]
#UseCase  Managing CORS, CSP, X-Frame-Options, and other Security HTTP Headers, Modifying the CloudFront Cache Key e.g. normalization, Redirecting Traffic Based on Simple Conditions and URL Rewrites and redirection.

### Solution Architectures

#### On-premises server requires a global distribution
[[Hybrid Cloud Architecture]] with CloudFront is possible. A custom origin can point to an on-premises server and CloudFront is able to cache content for dynamic websites. CloudFront can provide performance optimizations for custom origins even if they are running on on-premises servers. These include persistent TCP connections to the origin, SSL enhancements such as Session tickets and [[OCSP]] stapling. #performant 
Additionally, connections are routed from the nearest Edge Location to the user across the AWS global network. If the on-premises server is connected via a [[DX|Direct Connect]]  link this can further improve performance.

## References

1. [CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)
2. https://medium.com/trackit/cloudfront-functions-vs-lambda-edge-which-one-should-you-choose-c88527647695
3. https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cloudfront-limits.html