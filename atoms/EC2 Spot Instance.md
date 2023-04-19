* [Spot Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-requests.html)
	* 90% discount. Region, and AZ prices vary.
	* You will get 2-minute warning via [[EC2]] meta-data before shutdown. 
	* Spot Block - timeframe 1-6 hours of no interruption. Only valid for `one-time` requests - cannot be used for persistent requests.
	* Spot request: One-time or Persistent.
	* #UseCase: batch, data analysis, image processing, distributed workloads, flexible start and end times.
	* #antipattern Not suitable for critical jobs or databases.
	![[spot-instance-state-diagram.png]]
	* There are two types of spot requests: persistent and one-time. Refer to the state machine. 
```
{
  "MarketType": "spot",
  "SpotOptions": {
    "SpotInstanceType": "persistent"
  }
}
```
*  Cancel the spot request first, then cancel the spot instances. This way, new spot instances won't be created.
* [Spot Fleets](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-fleet-requests.html) 
	* Set of Spot Instance and Optional On-Demand Instances.
	* The spot fleet will try to meet the target capacity with price constraints.
	* Can have multiple launch pools, so that the fleet can choose. It will stop launching instances based on price constraints.
	* Automatic Scaling: Target tracking , Step (adjust based on size of alarm breach), scheduled. 
	* `request` and `maintain` are two types of spot fleets.