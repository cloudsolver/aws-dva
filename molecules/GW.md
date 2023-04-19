A [gateway](https://docs.aws.amazon.com/vpc/latest/userguide/extend-intro.html) connects your VPC to another network. For example, use an [internet gateway](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html) to connect your VPC to the internet. Use a [VPC endpoint](https://docs.aws.amazon.com/vpc/latest/privatelink/privatelink-access-aws-services.html) to connect to AWS services privately, without the use of an internet gateway or NAT device.

### Gateways on AWS
The gateway pattern is evident in AWS offerings.

#### API Gateway
[[API Gateway]] used for REST API and WebSockets for application architectures.

#### Internet Gateway
[[IGW]] used in [[VPC Connectivity]] to the Internet.

#### NAT Gateway
[[NATGW]] used to direct traffic [[VPC]]

#### Direct Connect gateways

[[DX|Direct Connect Gateway]]

---
#### Customer Gateway
[[CGW]] sits on the edge of the on-prem data center in a [[Hybrid Cloud Architecture]].

---
#### Virtual Private Gateway
[[VGW]]

#### Direct Connect Gateways
[[DGW]]

#### Transit Gateway
[[TGW]]


![[VGW DGW TGW.png]]
Fig. Comparison. [Source](https://www.megaport.com/blog/aws-vgw-vs-dgw-vs-tgw/)
>>>>>>> 4269e823efd1d66f7d89a511cc387cec5418459d
