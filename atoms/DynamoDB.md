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