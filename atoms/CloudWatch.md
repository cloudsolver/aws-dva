### Summary of CloudWatch
System-wide visibility into resource utilization, application performance, and operational health for every service. 
#AWSService 
### CloudWatch Details
- CloudWatch is basically a metrics repository. AWS services puts metrics in cloudwatch, custom metrics can be put in cloudwatch.
![[CloudWatch Metrics Alarms Notifcations Actions Architecture.png|512]]
- High resolution custom metrics and alarms support 1 second metrics

| Concept     | Description                                                                                                                                                                                                                                             |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Namespace   | A _namespace_ is a container for CloudWatch metrics.                                                                                                                                                                                                    |
| Metric      | A metric represents a time-ordered set of data points that are published to CloudWatch.                                                                                                                                                                 |
| Timestamp   | Each metric data point must be associated with a time stamp in UTC - Coordinated Universal Time                                                                                                                                                         |
| Dimension   | A _dimension_ is a name/value pair that is part of the identity of a metric. You can assign up to 30 dimensions to a metric.                                                                                                                            |
| Resolution  | Granularity of metric Standard = 1 min and High = 1 sec                                                                                                                                                                                                 |
| Statistics  | _Statistics_ are metric data aggregations over specified periods of time.                                                                                                                                                                               |
| Unit        | Each statistic has a unit of measure. Example units include `Bytes`, `Seconds`, `Count`, and `Percent`.                                                                                                                                    |
| Period      | A _period_ is the length of time associated with a specific Amazon CloudWatch statistic.                                                                                                                                                                |
| Aggregation | Aggregates statistics according to the period length that you specify e.g. Web hit latency aggregation every 60 seconds                                                                                                                                 |
| Percentile  | Percentiles are often used to isolate anomalies.                                                                                                                                                                                                        |
| Alarm       | You can use an _alarm_ to automatically initiate actions on your behalf. An alarm watches a single metric over a specified time period, and performs one or more specified actions, based on the value of the metric relative to a threshold over time. |

#### CloudWatch Integrations
| Timing         | Integration Type                      |
| -------------- | ------------------------------------- |
| Not Real Time  | S3 export is available after 12 hours |
| Near Real Time | Kinesis Data Firehose                 |
| Real Time      | Lambda                                |

_Subscriptions are filters that are applied to CloudWatch logs._ 

>**CloudWatch Subscription Architecture**
![[CloudWatch Subscription Architecture.png|512]]
Fig. Subscription Filter

> **CloudWatch Multi-Region Multi-Account**
![[Cloudwatch Multiaccount Subscription Filter Architecture.png|512]]
Fig. Subscription Filter across Regions stream to KDS then KDF for near real-time

> **Hybrid and EC2 CloudWatch Architecture**
> Requires a CloudWatch Agent (only logs), new CloudWatch Unified Agent (RAM, CPU, Disk, Network is out of the box for EC2)
> ![[CloudWatch Agent Architecture.png|256]]

> **CloudWatch Alarm Targets Architecture**
> Alarms should be sent to SNS from there subscribers can take any action.
> SNS subscriber can be a Lambda function, and it can use AWS SDK to pretty much do anything with the appropriate role.

**[[EventBridge]] Enables CloudWatch Integration**

**CloudWatch Dashboard Access**
- You can create a dashboard and give access via e-mail directly from AWS Console.
- CloudWatch>Dashboard>Select your board>Share Dashboard>Share your dashboard and require a username and password>Enter email address.
- 
**CloudWatch Insights**
Operational visibility into various workloads. 
| CloudWatch Insights | #UseCase                                                                                       |
| ------------------- | --------------------------------------------------------------------------------------------- |
| Container           | Aggregate logs and metrics from containers via CloudWatch agent within EKS, ECS, K8S, Fargate |
| Lambda              | Cold starts, lambda worker shutdown.                                                          |
| Contributor         | Top-N contributors based on CloudWatch logs                                                   |
| Application         | SageMaker driven to isolate ongoing issues. EventBridge and [[SSM Parameter Store]] OpsCenter integration         |



---
>  **References for CloudWatch**
	1.  https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Unified-Cross-Account.html
	2. https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html
	3. https://aws.amazon.com/about-aws/whats-new/2017/07/amazon-cloudwatch-introduces-high-resolution-custom-metrics-and-alarms/


*Created  2023-03-15 22:16*