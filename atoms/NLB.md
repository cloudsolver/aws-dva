Network Load Balancer is a type of [[ELB | Elastic Load Balancer]] that operates at layer 4. NLB does not terminate connections like the [[ALB]] does. NLB has no Security Group.
### Layer 4
Network Load Balancer operates at [Layer 4](OSI.md#Layer%204).
![Network Load Balancer diagram|250](https://s3.us-east-1.amazonaws.com/elb-polaris-cdk-assets-us-east-1-prod/2023-02-21T01-06-41_f711e1f2085536cdd2e5cf3814c3b7f9a49425fa46543744dace8418e82c80dc/Static/NLBdiagram.svg)
- Network: TCP, TLS (Secure TCP), UDP.
- Low latency ~100ms vs ~400ms for [ALB](ELB.md#ALB).
- High throughput with millions of requests per second. 
- Use it for extremely high performance.
- One static IP per AZ, and supports assigning Elastic IP
	- #UseCase whitelisting specific IP
- Designs
	- NLB can front a TG consisting of an ALB.
	- NLB can front a TG consisting of an on-prem IP and a private IP.
	- NLB can front a TG consisting of EC2 instances.
- Health Check: Supports TCP, HTTP/S protocols.
- NLB has an IPv4 address per [[Subnet]] in the AZ it is deployed to. So if you deploy to 3 AZs there will be 3 IP addresses.