Determine where network traffic from your subnet or gateway is directed.
Route Table belongs to a VPC and is associated with a [[Subnet]].
Once it is associated with a subnet, it will need Destination - Target Routes to be setup.
![[routes_destination_target_table.png]]
Fig. If Destination is 172.31.0.0/16 go to PCX - the peer connection.
In the example above, a route table connects to another VPC through a peering connection.


Subnet route table description
 [route tables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html) 