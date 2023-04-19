### VPC Gateway Endpoint
[[VPC]] [Gateway Endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/gateway-endpoints.html) do not require Internet or NAT - does not enable [[PrivateLink]] and are supported by [[S3]] and [[DynamoDB]] and don't cost anything.

### VPC to VPC Connectivity

#### Peering connections

- AWS-provided network connectivity between two VPCs.
- Use a [VPC peering connection](https://docs.aws.amazon.com/vpc/latest/peering/) to route traffic between the resources in two VPCs.
- VPC endpoints are do not work across Regions.
- VPC peering with updated route tables would work across cross-region VPC peering.
	- Reconfigure route table's target and destinations in the subnets.VPN

#### AWS Transit Gateway
[[TGW]] - AWS-provided regional router connectivity for VPCs
### Wavelength Zones
- You cannot have a VPC endpoints in a Wavelength zone.
#### Software Site-to-Site VPN

- Software appliance- based VPN connections between VPCs

#### Software Site VPN to AWS Managed VPN
- Software appliance to VPN connection between VPCs
- AWS managed high availability VPC VPN connection
- Supports a wide array of VPN vendors and products managed by you
- Supports static routes and dynamic BGP peering and routing

#### AWS Managed VPN
- VPC-to-VPC routing managed by you over IPsec VPN connections using your equipment

#### AWS Private Link
- AWS-provided network connectivity between two VPCs using interface endpoints.
![[PrivateLink]]
More information on [AWS Whitepaper](https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/amazon-vpc-to-amazon-vpc-connectivity-options.html)