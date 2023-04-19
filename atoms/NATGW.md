NATGW is created is an AWS managed NAT. Better choice than a [[NAT]] Instance. 

Offers higher bandwidth, high availability, no administration compared to a NAT Instance.

- EC2 instance in the same [[subnet]] can not use it. Only from another [[subnet]].
- Requires [[IGW | Internet Gateway ]]
	- Network path: Private [[Subnet]] => NATGW => IGW

### NAT Gateway versus NAT instance

| Quality                 | NATGW             | NAT Instance                         |
| ----------------------- | ----------------- | ------------------------------------ |
| Availability            | HA within AZ      | Needs scripting, failover setup      |
| Bandwidth               | 45 Gbps           | EC2 instance dependency              |
| Responsibility          | Managed by AWS    | Managed by customer                  |
| Cost                    | Per hour and data | Per hour EC2, networking - expensive |
| Public and Private IPv4 | Yes               | Yes                                  |
| Security Groups         | No                | Yes                                  |
| Use as Bastion Host     | No                | Yes                                  |
| Port Forwarding         | No                | Yes                                     |
NAT Instances must be set up in public subnets, disable Source/Destination check flags. 