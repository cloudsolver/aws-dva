### Summary of DynamoDB
Key-value schema-less database with single digit millisecond performance at any scale. #AWSService 
### DynamoDB Details
 - Primary Key and Sort Key are required, rest of the columns are infinite, and can expand in the future as needs evolve.
- 400 KB maximum item size
	- Not appropriate for BLOB storage, instead use pointers to S3. #antipattern 
 - **Provisioned Mode**
	 - RCU and WCU.
	 - Autoscales RCU and WCU.
	 - #UseCase gradual and predictable load.

#Q Describe WCU and RCU calculations.

|                      | WCU (1KB) | RCU (4KB) |
| -------------------- | --- | --- |
| Transactional        | 2   | 2    |
| Strongly Consistent  | 1   (standard) |  1   |
| Eventually Consistent |  n/a   | 0.5  (default)  |
**Table**. WCU/RCU across Consistency Modes

One _write capacity unit_ represents one write per second for an item up to 1 KB in size.
One _read capacity unit_ represents one read per second for an item up to 4KB in size.

**Formula**
![[DynamoDB RCU WCU Formula.png]]


Where, 

x = Size in KB; for Reads rounded up to a number divisible by 4
t = Transactions per second
μ = Capacity Unit Constant 1 for Write, 4 for Reads
Ω = Capacity Unit Factor (from Table Above)


#Q How do you calculate WCU?
**Answer**: WCU is 1KB per-item-second rounded upto the highest KB. e.g. 10 items per second each 4.5KB will be rounded to 10x5=50WCU. 120 writes per minute , each item is 3KB = 6WCU. Why? Remember to convert writes per minute to writes per second.
#Q What are the typical causes of `ProvisionedThroughputExceededException` , what options can be explored?
**Answer**: (1) Large Items Sizes (2) Hot Keys resulting in Hot Partition. Exponential backoff, use a better partition key that is better distributed.

#Q How is Write Sharding implemented?
Answer: It is an approach where the Primary key has a suffix or prefix added that can be random or generated with a hashing algorithm to prevent "hot" partitions.

#Q How does DynamoDB control Fine Grained Access Controls?
Answer: 

```
"Condition":{
	"ForAllValues:StringEquals": {
		"dynamodb:LeadingKeys":["${cognito-identity.amazon.aws.com:sub}"]
	}
}
```
Limits what users can see via LeadingKeys or Attrbutes.

---

#Q What is PartiQL used for?
Answer: DynamoDB provides a reduced SQL functionality to query data. Joins are not supported.

#Q What is the purpose and behavior of a GSI and LSI? 
Answer: GSI is literally another table that has a different Hash. It needs its own WCU and RCU. If it gets throttled, it will also throttle the main table. It can be added after the main table. LSI on the other hand must be selected during table creation time - max 5 per table. These act as alternative sort keys.

---

#Q How do you calculate RCU for Strongly Consistent and Eventually Consistent?
See: [Pricing](https://aws.amazon.com/dynamodb/pricing/provisioned/)
**Answer:** Get, BatchGet, Query and Scan needs a setting called `ConsistentRead` to enabled Strongly Consistent Reads. RCU is 4KB Item Read per Second. Eventually Consistent Reads are 0.5x needed RCUs. Example: 16 eventually consistent reads per second with 12KB Item size: 0.5x16x3=24 RCU. Example: 10 Strongly Consistent Reads per second 6KB = 10x8KB/4KB= 20 WCU.

#Q How can "hot key" for reads be solved ?
Answer: DAX will require no code changes. Multi-cluster, 5 min TTL, up to 10 nodes; 3 AZ recommended one node per AZ. Encryption at rest. Good for individual key caching. Use [[ElastiCache]] for complex objects that are not individual items. Port 9111 for encrypted traffic, or 8111 for unencrypted. It sets up [[EC2]] instances behind the scenes. A DAX cluster endpoint is created that the application will need to leverage.

#Q How does Optimistic Locking work?
Answer: By using an attribute on the table that can be used as a 'version number'. After an item is read and before it is updated, the version can be checked conditionally "Conditional Write" to ensure the version is still the same. At the time of the write, the version is updated.

#Q How does DynamoDB internally partition shards?
**Answer:** ![[DynamoDB Partitioning.png]]

---
#Q What are the options for  DynamoDB streams?
Answer:
NEW_IMAGE, OLD_IMAGE, NEW_AND_OLD_IMAGE, KEYS_ONLY.
KCL works for both Kinesis and DynamoDB streams. Streams will be sent only after it has been enabled.

---

#Q What consistency mode does GSI (Global Secondary Index) support?
Answer: Eventual Consistency.

---


	
 - **On-Demand Mode** 
	 - No capacity units but is much more expensive 
	 - #UseCase sudden spikes and unpredictable.

> **[[DR]]**
> 	Automated Backups: 35 Day continuous backup recovery window.
> 	New table is created upon restore of the Point in time backup.
> 	On-Demand Backups can be managed in [[AWS Backup]]. Backups are deleted manually.
> 	No impact to read capacity or performance of the operation system

### DAX
- DynamoDB Accelerator is a seamless in-memory cache.
- Microsecond latency for cached data on DynamoDB
- No application business logic changes required.
- DAX default TTL is 5 minutes.
#UseCase Single items from DynamoDB are requested repeatedly. Many cache technologies are available. Which one should be used? [[ElastiCache]] is better for aggregated queries. DAX is good for single item cache. 
### DynamoDB Stream Processing
- Item level modifications are streamed in order.
- #UseCase Real-time usage analytics; implement cross-region replication; insert into derivative tables and invoke [[Lambda]].
- #UseCase Alternatively, send events to [[Kinesis#Kinesis Data Stream]] and [[Kinesis#Kinesis Data Firehose]] to various services.
- Replication across regions is possible via Global Tables but it requires DynamoDB streams to be enabled.
### DynamoDB Global Tables
- Two-way replication across Regions.
- Accessible across regions via an active-active replication.

### Quiz
#Q You need to have a data storage layer in AWS. Following are the key requirements.
(a) Storage of JSON documents.
(b) Availability of Indexes
(c) Automatic scaling. 
What would be an ideal storage layer for the above requirements?
1. DynamoDB
2. EBS volumes
3. S3
4. Glacier
Answer: S3 does not support indexes. DynamoDB would work. I don't like the word 'storage' - as it is not usually considered a storage in the architectural sense.

#### References for DynamoDB
1. https://aws.amazon.com/dynamodb/

---
Created on 2023-03-13 14:37