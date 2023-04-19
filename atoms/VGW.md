A virtual private [[GW|gateway]] is the VPN endpoint on the Amazon side.

VGW attached to [[VPC]] =>[[ IPSec]] ([[VPN]]) over Internet => [[CGW]] or [[NAT]] on customer datacenter to establish  [[Site-to-Site VPN]] connection.

**Target gateway**: A generic term for the [[VPN]] endpoint on the Amazon side of the Site-to-Site VPN connection.
VPN concentrator on the AWS side of the VPN connection.
From the VPC - attach a VGW to enable a site-to-site VPN. Possibility to customize the [[ASN | Autonomous System Number]]