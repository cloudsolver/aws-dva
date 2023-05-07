### Summary of SNS
Simple Notification Service is a fully managed instantaneous pub/sub service for Application to Application and Application to Person messaging. It supports SMS text messages and MobilePush. #AWSService 
### SNS Details
- 100,000 topics, 12,500,000 subscribers per topic.
- Many Amazon Services connect to SNS e.g AWS Budgets, CloudFormation, [[ASG]], S3, Dynamo, DMS etc.
- SNS is both highly reliable and scalable, it provides significant advantages to developers who build applications that rely on real-time events.
- SNS can send `Email-JSON` for applications to read and process emails. Humans get text-based emails only.
- SNS Mobile Push lets you use SNS to deliver push notifications to Apple, Google, FireOS and Windows devices as well as Android.
#### Publishing Models
- Topic Publish
	- Create a topic
	- Create a subscription
	- Publish to the topic.
- Direct Publish
	- Create a platform application
	- Create a platform endpoint
	- Publish to platform endpoint
	- Various Mobile SDKs.
#### SNS Security
SNS Access Policies (similar to S3 bucket policies)
- Useful for cross-account access to SNS topics
- Useful for allowing other services ( S3…) to write to an SNS topic
- SNS supports [CloudTrail](CloudTrail) to get a history of SNS API calls made for security analysis.


### Solution Architectures
[[SQS]] can subscribe to [[SNS]] topics to fan-out. Each queue can have
![[Fan Out Options Architecture.png|512]]
Fig. Fan Out Best Practice 

SNS Fan-Out to [[SQS]] and [[Lambda]].
![](S3-SNS-SQS-Lambda%20Event.png)
Fig. S3 Event to Topic - SNS Fan-out to SQS and Lambda

**SNS FIFO Fan-Out to SQS FIFO**
![](SNS%20FIFO%20to%20SQS%20FIFO.png)
Fig. SQS FIFO subscribes to SNS FIFO topic

### References for SNS
1. https://aws.amazon.com/sns/
2. https://aws.amazon.com/sns/faqs/
3. https://docs.aws.amazon.com/sns/latest/dg/sns-mobile-application-as-subscriber.html

---
Created on 2023-03-10 22:11