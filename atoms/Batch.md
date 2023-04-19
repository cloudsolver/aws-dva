AWS Batch is an #AWSService that automatically provisions compute resources and optimizes the workload distribution based on the quantity and scale of the workloads.

It can run workloads on [[Docker]] including [[Fargate]] on [[ECS]]

- Job: Unit of work. Script, Linux executable, Docker image
- Job Definition: Describes how Jobs are to be run.
- Queue: Jobs are submitted here and it is associated with a computing environment.
[more on AWS](https://docs.aws.amazon.com/batch/latest/userguide/what-is-batch.html)