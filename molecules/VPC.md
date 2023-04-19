# Virtual Private Cloud (VPC)

A VPC is a virtual network that closely resembles a traditional network that you'd operate in your own data center. After you create a VPC, you can add subnets. [more on VPC overview](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)

* Foundational service that creates a private virtual network to launch resources.
* Spans [[AZ|Availability Zones]] in a region. [more on VPC config](https://docs.aws.amazon.com/vpc/latest/userguide/configure-your-vpc.html)
* VPC A and VPC B can be peered so they act as one logical VPC.You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account. The VPCs can be in different Regions (also known as an inter-[Region](Region.md) VPC peering connection). More on [peering](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html) 
* The default VPC always exists in every region in the account and has Internet connectivity. But all new VPCs are region specific. _Limit to 5 per region (soft)_

![[VPC Architecture.png]]
Fig. VPC Architecture

### Subnets

You can add two CIDR ranges to a [[Subnet]]. Tied to AZ. Public Subnet - connects to IGW.

[[NACL]] protects subnets. #secure 

[[SG | Security Groups]] protects EC2. #secure

### VPN
Site-to-Site VPN access can be created with a Virtual Private Gateway connection to a Customer Gateway in the customer data center.

### IP Addressing

![[IP Address]]
[[ENI]] is a logical component of a VPC that represents a virtual network card.

### Route Tables
Routing for subnets and gateways.
[[RouteTable]]

### Gateways

[[GW | Gateway]] and endpoints.

- See [[VPC Connectivity]] for more options on interconnecting VPN.

### VPC Traffic Mirroring

[Copy network traffic](https://docs.aws.amazon.com/vpc/latest/mirroring/) from network interfaces and send it to security and monitoring appliances for deep packet inspection.

### Transit [[GW]]

Use a [transit gateway](https://docs.aws.amazon.com/vpc/latest/userguide/extend-tgw.html), which acts as a central hub, to route traffic between your VPCs, VPN connections, and AWS [[DX]] connections.

### VPC Flow Logs

A [flow log](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html) captures information about the IP traffic going to and from network interfaces in your VPC.
VPC Flow Logs is a VPC feature that enables you to capture information about the IP traffic going to and from network interfaces in your VPC.

#### AWS VPN

Connect your VPCs to your on-premises networks using [AWS Virtual Private Network (AWS VPN)](https://docs.aws.amazon.com/vpc/latest/userguide/vpn-connections.html).


[[VPN]] is a Virtual Private Network.
[[ELB]] on AWS is at the edge of the VPC architecture.

### VPC Sharing
VPC sharing (part of Resource Access Manager) allows multiple AWS accounts to create their application resources such as EC2 instances, RDS databases, Redshift clusters, and Lambda functions, into shared and centrally-managed Amazon Virtual Private Clouds (VPCs). To set this up, the account that owns the VPC (owner) shares one or more subnets with other accounts (participants) that belong to the same organization from AWS [[Organizations]]. After a subnet is shared, the participants can view, create, modify, and delete their application resources in the subnets shared with them. Participants cannot view, modify, or delete resources that belong to other participants or the VPC owner.

### Quiz

#Q You have attached an Internet Gateway to your VPC, but your EC2 instances still don't have access to the internet. What is **NOT** a possible issue?
> a. Route Table
> b. SG ingress rules
> c. NACL egress rules
> d. EC2 only has a private IP
> e. NACL ingress rules for 1024-65535
> Answer: It is true that an EC2 instance cannot connect to the Internet (via IGW) when it does not have a public IP address. It is also true that without a route to the IGW within the subnet that the the EC2 instance is running, it will not be able to reach the internet. Finally, NACL needs to allow egress on 80 and 443 and allow ingress on ephemeral ports. That leaves us with SG ingress allow. Typically, when the Internet wants to reach EC2 - you need to allow SG ingress. In this case, EC2 wants to reach the Internet therefore it needs SG egress allow. Option b is SG ingress rules - this is a rule I would not check.  

#Q Which of the following VPC resources is highly available but not fault tolerant?
(a) Internet Gateway
(b) NAT Gateway
(c) VPC Gateway
(d) VPC Peering Connection
Answer: IG is fault tolerant, so is VPC Gateway and VPC Peering Connection.