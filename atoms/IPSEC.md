
IPSec adds encryption and authentication to make the Internet Protocol (IP) more secure. It scrambles the data at its source and unscrambles it at its destination. It also authenticates the source of the data. [Source](https://aws.amazon.com/what-is/ipsec/)
![[IPSec Modes.png|512]]
Fig. Modes [Source](https://www.twingate.com/blog/ipsec-tunnel-mode)

Site-to-Site [[VPN]] supports Internet Protocol security (IPsec) VPN connections.
-   **Transport**: IPSec transport mode encrypts only the data packet's payload and leaves the IP header in its original form. The unencrypted packet header allows routers to identify the destination address of each data packet. Therefore, IPSec transport is used in a close and trusted network, such as securing a direct connection between two computers.
    
-   **Tunnel**: An encrypted link where data can pass from the customer network to or from AWS. The IPSec tunnel mode is suitable for transferring data on public networks as it enhances data protection from unauthorized parties. The computer encrypts all data, including the payload and header, and appends a new header to it.
    
    Each VPN connection includes two VPN tunnels which you can simultaneously use for high availability.
    
    [[GW]]
    
