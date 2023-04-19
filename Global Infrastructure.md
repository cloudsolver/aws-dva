### Summary of Global Infrastructure

Amazon services are hosted in multiple locations world-wide. These locations are composed of AWS Regions, Availability Zones, Local Zones, AWS Outposts, and Wavelength Zones.
AWS Points of Presence (POP)
	  * 216 Points of Presence
	  * 205 Edge Locations
	  * 11 Regional Caches
	  * 84 cities across 42 countries
![AWS Region](AWS%20Region.md)

![AZ](AZ.md)

![Data Center](Data%20Center.md)

1. [Local Zones](https://aws.amazon.com/about-aws/global-infrastructure/localzones/)

* A Local Zone is an extension of an AWS [Region](Region.md) in geographic proximity to your users.
* Local Zones have their own connections to the internet and support AWS [[DX]], so that resources created in a Local Zone can serve local users with low-latency communications.
* Local Zones provide you the ability to place resources, such as compute and storage, in multiple locations closer to your end users.
* Use case: Run latency sensitive applications closer to the end users.

1. [Wavelength Zone](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-wavelength-zones)

* A Wavelength Zone is an isolated zone in the carrier location where the Wavelength infrastructure is deployed. Wavelength Zones are tied to a [Region](Region.md).
* A Wavelength Zone is a logical extension of a [Region](Region.md), and is managed by the control plane in the [Region](Region.md).

1. [Global Edge Network](https://aws.amazon.com/cloudfront/features/?p=ugi&l=na&whats-new-cloudfront.sort-by=item.additionalFields.postDateTime&whats-new-cloudfront.sort-order=desc)

* Amazon CloudFront peers with thousands of Tier 1/2/3 telecom carriers globally.
* CloudFront is well connected with all major access networks for optimal performance, and has hundreds of terabits of deployed capacity.
* CloudFront edge locations are connected to the AWS Regions through the AWS network backbone - fully redundant, multiple 100GbE parallel fiber that circles the globe and links with tens of thousands of networks for improved origin fetches and dynamic content acceleration.these are cached closest to audience.
* Mini-data centers created for low latency between applications and users.
* There are many more edge locations than AZs or regions.	

## Cloud Front
[[CloudFront]]

## Global Accelerator
[[Global Accelerator]]

https://infrastructure.aws