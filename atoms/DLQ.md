Dead Letter Queue (DLQ) is a queue where messages that can't be successfully processed go. 
*Amazon [[SQS]] does _not_ create the dead-letter queue automatically. You must first create the queue before using it as a dead-letter queue.* The dead-letter queue of a FIFO queue must also be a FIFO queue.

### DLQ Details
[[Lambda]] supports dead letter queues for [[SNS]], [[SQS]] and other events. You can configure a DLQ property and [[ARN]]. 

![[DQL-SQS.png]]
Fig. DLQ
#### References for DLQ
1. https://aws.amazon.com/about-aws/whats-new/2016/12/aws-lambda-supports-dead-letter-queues/

---
Created on 2023-03-13 12:52