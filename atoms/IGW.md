Internet [[GW|Gateway]] allows connectivity to the Internet by attaching to the [[VPC]] and route tables pointing to it from subnets.

It does require a route table entry without which it does nothing. So simply adding an IGW to the [[subnet]] will not give it connectivity to the Internet.

An [[EC2]] instance must be able to reach the IGW and have a public IP address to connect to the Internet. If you want your EC2 instance to be able to access the internet, you can assign it a public IP address.