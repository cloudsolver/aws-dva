Connection between your VPC and your own on-premises network i.e. [[Hybrid Cloud Architecture]]. Site-to-Site VPN supports Internet Protocol security ([[IPsec]]) VPN connections.
[More on AWS Site-To-Site VPN](https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html) 
Add more virtual private gateways to a [[VPC]] and enable [[ECMR]] to get higher bandwidth.

![[VPG_customer_gateway-NAT_corp_data_center_Hybrid_Cloud_context.png|256]]
Fig. Virtual Private Gateway needs Route Table propagation 

_Note: IPv6 is NOT supported on Site-To-Site VPN._

![[s2svpn-vgw-cgw.png]]
Fig. S2S VPN over the Internet IPsec Tunnel) to [[CGW]]

![[TGW-VPN-CGW.png]]
Fig. [[TGW|Transit Gateway]] over the Internet IPsec Tunnel to [[CGW]]

![[Multiple VPN to OnPrem.png]]
Fig. Multiple VPN from Virtual Private Gateway to CGW. You can add redundant CGW per location.

![[TGW to CGW over VPN.png]]
Fig. Transit Gateway to multiple customer datacenter.

![[VPN and DX.png]]
Fig. Customer Data Center to [[DX]] to VPN to VPG
![[Private connection via CGW-DX-TGW over VLAN.png]]
Fig. End to end private, secure and scalable