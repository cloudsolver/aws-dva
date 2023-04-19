### Summary of ALB
Application Load Balancer is a layer 7 load balancer that is fully managed [[ELB]].
### ALB Details

- A global accelerator can provide it a fixed IP address. You CAN'T assign an Elastic IP. The other alternative is to front it with an [[NLB]] and assign it an Elastic IP or BYOIP (Bring your own IP). 
- Web ACL from [[WAF]] in the same region can be attached for protection. #secure 

![Application Load Balancer diagram|250](https://s3.us-east-1.amazonaws.com/elb-polaris-cdk-assets-us-east-1-prod/2023-02-21T01-06-41_f711e1f2085536cdd2e5cf3814c3b7f9a49425fa46543744dace8418e82c80dc/Static/ALBdiagram.svg)

#### Application Load Balancer
- ALB: [Layer 7](OSI.md#Layer%207): HTTP, HTTPS, WebSocket
- Fixed hostname e.g. xyz.region.elb.amazonaws.com
- EC2 don't see IP of the client - ALB injects a header `X-Forwareded-For` along with `X-Forwarded-Port` and `X-Forewarded-Proto`
- Routing Tables to different target groups based on:
	- path in URL
	- hostname in URL
	- query strings
	- headers
#UseCase microservices, container-based applications. Port mapping features are useful.
- Target Groups
	- EC2 Instances (can be managed by an [[ASG]] - HTTP
	- EC2 tasks (managed by [[ECS]]) - HTTP
	- [[Lambda]] functions - HTTP request is translated into JSON event.
	- IP address - must be private IPs.
	- ALB can route to multiple target groups.
	- Health checks at the Target Group level.

A listener is a process that checks for connection requests using the port and protocol you configure. The rules that you define for a listener determine how the load balancer routes requests to its registered targets.

#Q An application is deployed with an Application Load Balancer and an Auto Scaling Group. Currently, you manually scale the [[ASG]] and you would like to define a Scaling Policy that will ensure the average number of connections to your EC2 instances is around 1000. Which Scaling Policy should you use?
(a) Simple Scaling Policy
(b) Step Scaling Policy
(c) Target Tracking Policy
(d) Scheduled Scaling Policy
Answer: Target Scaling Policy.

#Q A company needs to capture all client connection information from its Application Load Balancer every five minutes. This data will be used to analyze traffic patterns and troubleshoot the application. 
(a) Enable CloudTrail for the ALB
(b) Enable access logs on the ALB
(c) Install CloudWatch agent on the ALB
(d) Enable CloudWatch logs
Answer: This is a good question. Basically, you need to see access logs so that is what you need to enable.

### Constraints

**An Application Load Balancer cannot be assigned an Elastic IP address** (static IP address). However, a Network Load Balancer can be assigned one Elastic IP address for each Availability Zone it uses. 
If you need a static IP address for your Application Load Balancer, it's a best practice to **register the Application Load Balancer behind a Network Load Balancer**. The static IP address assigned to a Network Load Balancer doesn't change, providing a fixed entry point for your Application Load Balancer. #BestPractice 

---
**References for ALB**
1. https://aws.amazon.com/elasticloadbalancing/application-load-balancer/ 
 
*Created on 2023-03-20 12:39*