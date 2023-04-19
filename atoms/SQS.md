### Summary of SQS
Exchange messages via at-least-once delivery, best-effort ordering, low-latency, small size, [[FIFO]] messages between distributed applications that employs a polling method. #AWSService 
### SQS Details
- At-least-once delivery and best-effort ordering.
- `SendMessageAPI` to send to SQS. Default message retention period 4 days. Maximum retention is 14 days.
- Low Latency < 10ms, Limitation of 256 KB message size.
- Consumer may receive up to 10 messages at a time. `ReceiveMessage` will get the same message again unless `DeleteMessage` is invoked. 
- If `MessageVisibility` timeout of 30 seconds expires, SQS Queue will deliver a different message to different consumer.
![[SQS Polling]]
- FIFO - exactly once processing (delivered once and remains available until processed by consumer). Q name must end with `.fifo` . Max 300 msg/second and 3K msgs/second with batching. Max 20K in-flight messages at a time *no errors reported if quota breached - must monitor and alert* `ApproximateNumberOfMessagesNotVisible` is a available CloudWatch metric.
![Visibility|500](https://docs.aws.amazon.com/images/AWSSimpleQueueService/latest/SQSDeveloperGuide/images/sqs-visibility-timeout-diagram.png)
- Amazon SQS allows you to retain messages for days and process them later, while we can take down our EC2 instances.
#### SQS Security
- Encryption: Supports HTTPS with TLS and encrypts message using SSE with [[KMS]] for storage before it is decrypted and sent to the requesting consumer that is authorized.
- Access: IAM policies regulate access to SQS API. SQS Access Policies (similar to S3) are useful for cross-account access to SQS queues. Useful for allowing other services to write to an SQS Queue.

### Solution Architectures
#### Scale EC2 Horizontally
Queue Depth measured by CloudWatch triggers an alarm that can request [ASG](ASG.md) to add more EC2 instance #performant and #resilient .
![[QueueDepthAutoScaling.png]]
Fig. Auto scale [[EC2]] via [[ASG]] based on [[CloudWatch]] Alarm
The underlying databases should be able to handle the load as well or throttled with limited connections in the pool.  
#UseCase 

#### Prioritize Queues
Just use standard SQS queues. FIFO queues will not be helpful. The application tier should be able to prioritize polling logic to poll more frequently from the paid queue.

#### Decouple Front End Web from Back End
![](sqs-decouple-architecture.png)
#### References for SQS
1. https://aws.amazon.com/sqs/faqs/

---
Created on 2023-03-10 07:47