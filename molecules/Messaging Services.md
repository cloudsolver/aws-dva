
#### Kinesis vs SQS ordering
Assume 100 trucks sending GPS data, 5 kinesis shards versus SQS FIFO

| [[Kinesis]] | [[SQS]] FIFO |
|---|---|
|20 trucks per shard | One SQS.FIFO 
| Data ordered within assigned shard | 100 Group ID
| 5 Max Consumers in parallel | 100 Consumers based on 100 Group IDs 
| Can receive up to 5MiB/Second | 300 messages or 3K per second

SQS makes sense to have dynamic consumers. However, Kinesis makes sense for 1000s of trucks.

#### SQS v SNS v Kinesis

| [[SQS]] | [[SNS]] | [[Kinesis]]|
|---|---|---|
| No need to provision throughput | No need to provision throughput | Must provision throughput or on-demand capacity|
| Unlimited consumers | 100K topics 12.5M subscribers| Kinesis Firehose writes data
| Ordering guarantees only on FIFO queue | FIFO capability for SQS FIFO | FIFO per shard |
| Poll | Push | Standard pull, enhanced fan-out - push|