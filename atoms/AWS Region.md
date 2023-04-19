## Summary
An AWS Region is a distinct geographic area that contains logical data centers called Availability Zones [AZ](AZ.md), Local Zones, and Wave Length Zones.
## AWS Region Details

* Is a separate geographic area. Therefore if one is impacted by a natural disaster, chances are that another will not.
* Regions are fully independent.
* Services and resources vary by [region](Region.md).
* No automagic replication across regions.
* What factors influence the selection of an AWS [Region](Region.md)? 
	* Compliance: regulations.
	* Proximity to reduce latency.
	* Available Services: Feature vary by region.
	* Pricing: Prices vary from region to region.

## References
1. [Region](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html)