A [subnet](https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html) is a range of IP addresses in your [[VPC]]. A [[Subnet]] must reside in a single [[AZ]]. After you add subnets, you can deploy AWS resources in your [[VPC]].

Subnets are not isolation boundaries around your application. Rather, they are containers for routing policies

### IPv6 Subnet Design
![](https://d2908q01vomqb2.cloudfront.net/fc074d501302eb2b93e2554793fcaf50b3bf7291/2019/10/10/spicer3.png)
Fig. Multi-AZ IPv6 Subnet
[Source](https://aws.amazon.com/blogs/architecture/one-to-many-evolving-vpc-design/)