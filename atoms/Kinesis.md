### Summary of Kinesis
Collect, process, and analyze real-time video and data streams. #AWSService 
### Kinesis Details
- Kinesis Data Streams: ingest and store data streams for processing.
- Kinesis Data Firehose: extract, transform and load service for streaming data to data lakes, stores and analytics services.
- Kinesis Data Analytics: Apache [[Flink]] or SQL to analyze and transform streaming data.
- Kinesis Video Stream - camera devices secure stream video to AWS using Kinesis Video Streams SDK to be ingested, encrypt, durably store and index for real-time and batch analysis.
#### Kinesis Data Stream
![[Stream.png]]
Fig. Stream
- Real-time (~200ms latency). 
- Retention 1 day to 365 days.
- Immutable data - can't be deleted but can be replayed
![](kinesis-data-stream-producer-consumer-architecture.png)
- Provisioned Mode: 1MiB/Second/Shared Write with 2MiB/Second/Shard. Pay per shard provisioned per hour.
- On demand: Up to 200MiB/second write and 400MiB/second read.
![](Kinesis%20Shard%20On-Demand%20or%20Provision.png)
#### Kinesis Data Firehose
![[firehost-photo.png]]
Fig. Firehose
- Firehose knows how to write data to [[S3]], Redshift (copied from S3), [[OpenSearch]]. Can send data to 3rd party like Datadog, Splunk, New Relic, mongoDB.
- Near-Realtime (buffer time min 60 seconds). No need to write your own code.
- Transform data with [[Lambda]], convert data format - [[Parquet]], ORC etc.
- Buffer Interval - flushes at this interval.
![](Kinesis%20Data%20Firehose%20Conceptual.png)

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


---
**References for Kinesis**
1. https://aws.amazon.com/kinesis/data-streams/?nc=sn&loc=2&dn=2

---
Created on 2023-03-10 22:46