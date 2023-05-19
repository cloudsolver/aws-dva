### Summary of Kinesis
Collect, process, and analyze real-time video and data streams. #AWSService 
### Kinesis Details
- Kinesis Data Streams: ingest and store data streams for processing.
- Kinesis Data Firehose: extract, transform and load service for streaming data to data lakes, stores and analytics services.
- Kinesis Data Analytics: Apache [[Flink]] or SQL to analyze and transform streaming data.
- Kinesis Video Stream - camera devices secure stream video to AWS using Kinesis Video Streams SDK to be ingested, encrypt, durably store and index for real-time and batch analysis.
#### Kinesis Data Stream (Real-Time)
![[Stream.png]]
Fig. Stream
- Real-time (~200ms latency). 
- Retention 1 day to 365 days.
- Immutable data - can't be deleted but can be replayed
![](kinesis-data-stream-producer-consumer-architecture.png)
- Provisioned Mode: 1MiB/Second/Shared Write with 2MiB/Second/Shard. Pay per shard provisioned per hour.
- On demand: Up to 200MiB/second write and 400MiB/second read.
![](Kinesis%20Shard%20On-Demand%20or%20Provision.png)
#### Kinesis Data Firehose (Near Real-Time)
![[firehost-photo.png]]
Fig. Firehose
![[Kinesis Data Firehose]]

#### Data Stream versus Firehose
| Data Stream| Firehose|
|---|---|
| Create Data Stream | Create Delivery Stream |
| Streaming for ingest at scale| Load streaming data into various AWS services and 3rd party |
| Custom Code for producer and consumer | Fully Managed |
| Real-Time ~200ms| Near Real-Time 60s buffer|
| Data storage 1-365 days| No storage|
| Supports Replay | No support for Replay|


#### Kinesis Security
- Controls access using IAM. HTTPS, KMS and CloudTrail supported

### Solution Architectures
#UseCase A company provides a REST-based interface running on EC2 instances that allows a partner company to send data in near-real time. How do you scale?
Any near-real time solution must utilize Kinesis. Other messaging solutions will work however will not meet the "near real-time" requirement.

#Q  Kinesis can be written at 1MB/Sec or 1000 messages. How is ProvisionedThroughputExceeded exception remediated?
See: [Blog Post](https://repost.aws/knowledge-center/kinesis-readprovisionedthroughputexceeded)
**Answer**: Retry with Exponential Backoff, Increase the number of shards, pick a highly distributed shard key. 

#Q What are the various capacity modes for Kinesis Data Stream?
See: [DG](https://docs.aws.amazon.com/streams/latest/dev/how-do-i-size-a-stream.html)
Answer: Provisioned and On-Demand. 
	Provisioned.
	- Use Provisioned to save cost and have predictable workload. 
	- 1MB/Sec in
	- 2MB/Sec out (Classic and Fan Out consumer)
	- Pay per shard-hour
- On-Demand
	- 4MB/Sec default for Incoming.
	- Pay per stream-hour + Data In/Out per GB.
	- Expensive but no need to provision and scaled automatically.

#Q What are the Consumer  Modes for Kinesis Data Streams?
See:
Answer:
| Shared Fan-Out Consumer                        | Enhanced Fan-Out Consumer  |
| ---------------------------------------------- | -------------------------- |
| Pull                                           | Push                       |
| 2MB per shard across consumers                 | 2MB per shard per consumer |
| Latency ~200ms                                 | Latency ~70ms              |
| Low Cost                                       | High Cost                  |
| Consumer Polls                                 | Kinesis Pushes HTTP/2      |
| GetRecord API                                  | SubscribeToShard API       |
| Returns up to 10MB then throttle for 5 seconds | Up to 5 consumers per data stream (soft limit)                           |

#Q How does Lambda consume Kinesis Data Stream?
See:
Answer: It uses the `GetBatch` API to get up to 10 batches per shard.
![[Kinesis Lambda Consumer.png]]
Fig. Lambda Kinesis GetBatch

#Q How are cold and hot shards tackled relative to scale-out and scale-in ? What are the cost and data retention implications?
See:
Answer:  Hot shard is split into two. Old shards are deleted after messages expire. Two Cold Shards are merged into one. Cold shard is closed for writes and is deleted after messages expire.


---
**References for Kinesis**
1. https://aws.amazon.com/kinesis/data-streams/?nc=sn&loc=2&dn=2

---
Created on 2023-03-10 22:46