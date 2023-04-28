
| Scaling Policy  | Description                                                                                                            |
| --------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Simple          | The first scaling policy on AWS. No fine-grained controls. CloudWatch alarm can trigger a % increase in capacity. Not supported on ECS.     |
| Target Tracking | Recommended - especially for CPU metrics. Set the target metric and the scaling group expands or contracts to meet it. |
| Step            | Useful when ASG continues to react to alarms with no cool down wait.                                                   |
| Scheduled       | ECS tasks scaled based on date and time.  Not supported on EC2 ASG.                                                                                                                      |

