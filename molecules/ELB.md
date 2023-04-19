Elastic Load Balancers is an #AWSService that can be set up externally as well as internally.
## CLB
![[CLB]]
#### ALB
![[ALB]]
## NLB
![[NLB]]
## GWLB
![[GWLB]]
## Session Affinity
- Implement same client is always directed to the same instance behind a load balancer.
- Possible via CLB and ALB via `cookie` that has an expiration date.
### Application Based Cookies
- Custom Cookie : don't use reserved cookie names e.g. `AWSALBTG`
- Application Cookie `AWSALBAPP` 
### Duration Based Cookies
- Load Balancer Generate `AWSALB` or `AWSELB` (Classic)
You can configure this in the Target Group settings.

## Cross-Zone Load Balancing
- With Cross-Zone Load Balancing enabled - each EC2 instance will get same load.
- Without Cross-Zone Load Balancing each AZ gets equal load regardless of EC2 capacity.
- [[ALB]]: Enabled by default. No charge.
- [[CLB]]: Disabled by default. No charge for enabling.
- [[NLB]] and [[GWLB]]: Disabled by default. Charges for enabling inter-AZ traffic.

## Security
- Perfect Forward Secrecy [[PFS]] is supported to safeguard against eavesdropping of encrypted data.

### SSL and TLS  

HTTPS listener 
	You must specify a default certificate. 
	You can add an optional list of certs to support multiple domains.
	Clients can use [[SNI]] (Server Name Indication) to specify the hostname 
Constraint: Does not work with CLB. Only works with ALB, NLB and CloudFront.
ALB v2 and NLB v2 supports multiple listeners with multiple SSL certificates and uses SNI.
CLB v1 supports only 1 SSL certificate.

## Connection Draining
Time to complete 'in-flight requests' while the instance is de-registering or unhealthy. Stops sending new request to the EC2 instance which is de-registering. During this time new connections to ELB are directed to healthy instances.
Default: 300 seconds. Set to lower values for shorter requests.

## General Notes

- Load Balancer security group should allow users to connect from anywhere via HTTP/S however the EC2 behind it should only allow traffic coming from the load balancer. How? By linking the security group of the EC2 to the load balancer security group as *source* rather than a CIDR.
- #Q For compliance purposes you would like a fixed static IP address to your end-users so they can write firewall rules that will be stable and approved by regulator. What type of ELB would you choose?
	- ALB with an Elastic IP attached to it?
	- NLB?
	- CLB?
	- Answer is NLB. An Elastic IP cannot be attached to an ALB. However, an NLB gets a public IP address on each AZ.