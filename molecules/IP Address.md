You can assign IPv4 addresses and IPv6 addresses to your VPCs and subnets. You can also bring your public IPv4 and IPv6 GUA addresses to AWS and allocate them to resources in your VPC, such as [EC2](EC2.md) instances, NAT gateways, and Network Load Balancers.

### CIDR
![[CIDR]]

### Private IPv4
[[IANA]] established certain blocks of IPv4 for LAN and Internet.

- 10.0.0.0/8
	- for big networks
- 172.168.0.0/12
	- AWS default VPC in that range
- 192.168.0.0/16
	- home networking
All the rest of IP addresses on the Internet are public.

### Network ID
**The portion of an IP address that identifies which TCP/IP network the host resides on**. Performing a bitwise AND operation between the IP address and the [[subnet]] mask.

### Broadcast ID
When data is sent to the broadcast address, it is received by every device on that network. The broadcast ID is typically assigned as the last address in a network range.