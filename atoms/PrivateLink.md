AWS PrivateLink is a highly available, scalable technology that enables you to privately connect your VPC to services as if they were in your VPC.

Establish connectivity between VPCs and AWS services without exposing data to the Internet.

![](https://docs.aws.amazon.com/images/vpc/latest/privatelink/images/use-cases.png)
https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html

#UseCase **Consumer-Service Provider Pattern**. Consumer application in a VPC should connect to another VPC's NLB to access application interface without traversing the Internet.
![](https://docs.aws.amazon.com/images/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/images/aws-privatelink.png)
Fig. PrivateLink can be used when Peering cannot due to overlapping CIDRs