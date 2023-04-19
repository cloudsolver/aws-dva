### Summary of Hybrid Cloud Architecture
**Hybrid cloud architecture** is the combination of public and [private clouds](https://www.vmware.com/topics/glossary/content/private-cloud.html) by a wide area network or broadband connection, through which applications and data can be shared and which can be managed as a single IT architecture.

(a) Connect over the Internet
(b) Connect over VPN
(c) Connect over Direct Connect


### Hybrid Cloud Architecture Details

#UseCase It is well suited to fluctuations in demand for computing resources since it enables businesses to scale from on-premises to public cloud-based to meet increased demand, and scale back from the [public cloud](https://www.vmware.com/topics/glossary/content/public-cloud.html) to on-premises (private cloud) only once demand recedes.

- Customer Gateway on the on-prem data center and a virtual private gateway on AWS is required

![[site-to-site_VPN_API_Gateway_CloudFront_Route53_context.png]]
Fig. Customer Gateway and VPGW
## Network to AWS VPC
[[VPC]] connectivity from other clouds or on-prem requires various architectural considerations. [AWS Whitepaper PDF](https://docs.aws.amazon.com/pdfs/whitepapers/latest/aws-vpc-connectivity-options/aws-vpc-connectivity-options.pdf#introduction)



### Site-to-Site VPN
Customer Gateway Device (On-premise)
- Install [[CGW | Customer Gateway]]
- Decide on IP Address
	- Public Internet-routable
	- [[NAT]]-T (NAT Traversal) public IP fronting the [[CGW]]
- Routing
	- Route Table propagation in each route table within a [[subnet]] must be enabled.
	- Ping requires [[ICMP]] protocol in Security Group to be enabled.
[[VGW | Virtual Private Gateway]]

### Use Cases for Hybrid
- Cloud Bursting
	- Storage and compute bursting in the cloud
- Global Reach
	- Use S3, CloudFront and other services on the edge and other regions.

### VMWare Cloud expanded to AWS
A company that is already running VMWare on premise can expand into AWS.
![[VMWare on AWS Cloud Architecture.png]]
Fig. VMWare Cloud on AWS

#### References for Hybrid Cloud Architecture
1. https://docs.aws.amazon.com/whitepapers/latest/hybrid-cloud-with-aws/hybrid-cloud-with-aws.html


###### Timestamp
---
Created on 2023-03-14 16:52