## Summary
It directs global traffic via closest edge locations and **Anycast** IP through internal Amazon network to reduce latency, improve performance and network stability.  #AWSService 
## Global Accelerator Details
- Makes your application go global. #WellArchitected 
- Enables [[DR| disaster recovery]] and failover to another region's [[ALB]]. #resilient  
- Improve performance and stability. Application is deployed in one region, however there are users all over the world. How can global users work on the app without going through the Internet across so many hops? To minimize **latency**.
- Two [[Anycast]] IPv4 addresses are created and a DNS entry are provided with the creation of the Global Accelerator. Dual-Stack IP Addresses are supported as well.
- Leverage AWS global network from the edge location to the public ALB via AWS private network. 
- Global Accelerator is a good fit for non-HTTP use cases, such as gaming (UDP), IoT (MQTT), or [[VOIP]] Voice-over-IP.
**Unicast**: one server one IP.
**Anycast** IP: all servers hold the same IP address and the client is routed to the nearest one.

Supported: ElasticIP, [[EC2]], [[ALB]], [[NLB]].

The static addresses are advertised globally using anycast from the AWS edge network to your endpoints.
- You can point your custom domain name to the IP address or the DNS name of the global accelerator.
- Now when a client makes a request using your custom domain name, the DNS server resolves it to the IP addresses, in random order, or to the DNS name for your accelerator.
- #UseCase Blue/Green deployments when DNS server results are usually cached by clients. Portion of traffic can be moved.
- For real-time streaming and on-demand videos [[CloudFront]] is a better option (not Global Accelerator).

#### Security
- Only 2 external IP need to be whitelisted.
- DDoS protection from AWS [[Shield]]
### Types of Global Accelerator
There are two types: standard and custom routing.
#### Standard Accelerator
- Simply directs traffic to optimal endpoints over the AWS global network to improve the availability and performance of your Internet.
- Each accelerator includes one or more listeners. 
- A listener processes inbound connections from clients to Global Accelerator.
#### Custom Routing
*A custom routing accelerator maps listener port ranges to EC2 instance destinations in virtual private cloud (VPC) subnets. This allows Global Accelerator to deterministically route traffic to a specific Amazon EC2 private IP address and port destination in your [[subnet]].*
Note: Global Accelerator **does not** perform health checks for custom routing accelerators and does not failover to healthy endpoints. Traffic for custom routing accelerators is routed deterministically, regardless of the health of a destination resource.
## References

1. [Types of Global Accelerators](https://docs.aws.amazon.com/global-accelerator/latest/dg/introduction-accelerator-types.html)
2. [Custom Routing](https://docs.aws.amazon.com/global-accelerator/latest/dg/about-custom-routing-how-it-works.html)
3. [Custom Routing Guideline](https://docs.aws.amazon.com/global-accelerator/latest/dg/about-custom-routing-guidelines.html)