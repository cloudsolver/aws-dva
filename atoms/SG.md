Security Group is a stateful firewall for [[EC2]] instances. 
EC2 instance firewall #secure . These are stateful and do not require ephemeral port considerations on the outbound.
- Reachability Analyzer: performs network connectivity testing between AWS resources.

Only Allow Rules. No deny rules. SG cannot block IP addresses, but you can limit the allow range to know IPs.

Inbound and outbound traffic is paired at the port/IP level. 

Many instances can share a security group.
SG is locked down to a [Region](Region.md)/[[VPC]] combination.
#BestPractice maintain one separate security group for [[SSH]] access.
If application is not accessible, it is a security group issue. If your application returns an error such as 'connection refused' it's actually an application error or it's not launched.
All inbound traffic is blocked by default. 
All outbound traffic is authorized by default.
Security Groups can authorize other security groups  without thinking about IP. 

Privileged [[Ports]] are required to be memorized.