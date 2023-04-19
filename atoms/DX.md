AWS Direct Connect makes it easy to establish a dedicated connection from an on-premises network to one or more VPCs in the same region. Using private [[VIF]] on AWS Direct Connect, you can establish private connectivity between AWS and your data center, office, or co-location environment, as shown in the following figure. #AWSService 

### Connectivity
One end of the cable is connected to your router, the other to an AWS Direct Connect router. With this connection, you can create _virtual interfaces_ directly to public AWS services (for example, to Amazon S3) or to Amazon VPC, bypassing internet service providers in your network path. [source](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html)
![[DirectConnectDiagram.png|512]]
Fig. Direct Connect VIF, VLAN
- Supports 1Gbps and 10Gbps bandwidth

Steps on how to set up a Direct Connect with AWS:

1.  **Choose a Direct Connect partner.** There are many companies that offer Direct Connect services, so you'll need to choose one that meets your needs. Some factors to consider include the cost of the connection, the speed of the connection, and the level of support offered. e.g. Amazon, Equinix, Inteliquent, Level 3 Communications, Tata Communications etc.
2.  **Configure your Direct Connect connection.** Once you've chosen a Direct Connect partner, you'll need to configure your connection. This includes providing information such as your AWS account ID, the region of your AWS environment, and the bandwidth you need.
3.  **Install the Direct Connect hardware.** Once your connection is configured, you'll need to install the Direct Connect hardware. This includes a router and a transceiver. The router will connect to your on-premises network, and the transceiver will connect to the Direct Connect hub.
4.  **Connect to AWS.** Once the Direct Connect hardware is installed, you can connect to AWS. This can be done by using a VPN or by using the AWS Direct Connect console.

Here are some benefits of using Direct Connect:

-   **Increased bandwidth and lower latency.** Direct Connect provides a dedicated connection between your on-premises network and AWS, which can increase bandwidth and lower latency.
-   **Improved security.** Direct Connect provides a private connection between your on-premises network and AWS. It is not encrypted.
-   **Cost savings.** Direct Connect can save you money on bandwidth costs.
-   **Flexibility.** Direct Connect can be used to connect to a variety of AWS services.

Here are some drawbacks of using Direct Connect:

-   **Initial investment.** Direct Connect requires an initial investment in hardware and software.
-   **Complexity.** Direct Connect can be complex to set up and maintain.
-   **Vendor lock-in.** Once you choose a Direct Connect partner, you're locked into that partner for the life of the connection.

Overall, Direct Connect is a great option for businesses that need a reliable, secure, and cost-effective way to connect to AWS.
https://aws.amazon.com/directconnect/

### High Resiliency with DX
A highly resilient [[Hybrid Cloud Architecture]] can be designed by connecting multiple DX connections at multiple DX locations to AWS Region.
![[Multiple DX to Region.png]]
Fig. Direct Connect from multiple customer datacenters

### Direct Connect Gateway
![[DGW]]

### Quiz
#Q You have set up a Direct Connect connection between your corporate data center and your VPC A in your AWS account. You need to access VPC B in another AWS region from your corporate datacenter as well. What should you do? Answer: Use  a direct connect gateway.
#Q An organization is extending a secure development environments into AWS. They have set up a Direct Connect connection. What else needs to be done to add encryption? Answer: Setup a VPG over DX to enable IPSec encryption. Alternatively, use [[MACsec]] (MAC Security) that provides confidentiality, integrity and origin authenticity.