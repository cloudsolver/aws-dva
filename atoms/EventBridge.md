## Summary
Build loosely coupled event driven architecture at scale with Event Bridge. #AWSService 

## EventBridge Details
- Create a custom [event bus](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-bus.html) to receive [events](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-events.html) from your applications. 
-  Applications can also send events to the default event bus. When you create an event bus, you can attach a [resource-based policy](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-use-resource-based.html) to grant permissions to other accounts.
- Event Bridge can have a rule to run an [[ECS]] task. (requires ECS Task Role)
>**EventBridge Event Bus versus Event Bridge Pipe**
> 	EventBridge event buses are well suited for many-to-many routing of events between event-driven services.
> 	 [EventBridge Pipes](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-pipes.html) is intended for point-to-point integrations between these [sources](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-pipes-event-source.html) and [targets](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-pipes-event-target.html), with support for advanced transformations and [enrichment](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-pipes.html#pipes-enrichment).
 #### Resource based and identity based policies.
 For Kinesis streams, EventBridge uses [identity-based](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-use-identity-based.html) policies.
 For Lambda, Amazon SNS, Amazon [[SQS]], and Amazon CloudWatch Logs resources, EventBridge uses resource-based policies. [More](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-use-resource-based.html)

> **Complex Log Event Processing with [[EventBridge]]**
> Possible to set up a cron job. Also, set up security triggers e.g. notification email when root user logs in to console.
> (a) Default Event Bus - provided within the AWS account. (b) Custom Event Bus - create a separate event bus, and (c) Partner Event Bus e.g. Data Dog, Zen Desk etc.
> ![[Source-Destination Event Bridge Architecture.png|512]]
> Fig. Event Bridge Architecture with [[CloudWatch]]
> Support for event schema discovery within its Schema Registry feature along with versioning
> Manage permissions into the Event Bus. #UseCase Aggregate all events into a central bus from all accounts within an organization.
> ![[AWS events from other account.png]] 
> You could create a bus by environment, organization unit and critical application or path.

## References

1. [AWS Event Bridge](https://aws.amazon.com/eventbridge/) 
2. https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-create-event-bus.html