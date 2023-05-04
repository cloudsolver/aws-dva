- Firehose knows how to write data to AWS, 3rd Party and your Custom Endpoints (HTTPS). Pay for data only.
- [[S3]], [[Redshift]] (copied from S3), [[OpenSearch]]. 
- Can send data to 3rd party like Datadog, Splunk, New Relic, MongoDB.
- Near-Realtime (buffer time min 60 seconds or 1MB of data). No need to write your own code.
- Transform data with [[Lambda]], convert data format - [[Parquet]], ORC etc.
- Buffer Interval - flushes at this interval.
![](Kinesis%20Data%20Firehose%20Conceptual.png)
