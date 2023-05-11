**#Q What are the key features of the #AWSService : Step Functions?**
*See*: [Home Page](https://aws.amazon.com/step-functions/)
**Answer**: Coordinates the components of distributed applications and microservices using visual workflows. Model Workflows in JSON. Visualize model, execution and history. Start workflows with SDK, [[API Gateway]], [[EventBridge]] etc.

**#Q What are the common use cases for step functions?**
*See*: [FAQ](https://aws.amazon.com/step-functions/faqs/) 
**Answer**: Automate ETL, IT functions such as DevOps, orchestrate large scale parallel workflow like ML and microservices. Workflows that allow for human approval.

**#Q What are the various state types in the Step Functions state machine?**
*See*: [Dev Docs](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-states.html)
**Answer**: _States_ are elements in your state machine. A state is referred to by its _name_, which can be any string, but which must be unique within the scope of the entire state machine.
States can perform a variety of functions in your state machine:

| Type           | Description |
| -------------- | ----------- |
| Task           |      Do some work in your state machine        |
| Choice         | Make a choice between branches of execution            |
| Fail / Succeed |   Stop an execution with a failure or success             |
| Pass           |  Pass its input to its output, or inject some fixed data into the workflow           |
| Wait           |   Delay for a certain amount of time, or until a specified date and time         |
| Parallel       |   Begin parallel branches of execution           |
| Map               |Dynamically iterate steps            |

Table. State Types and Description

#Q How can we setup polling for tasks via [[ECS]] or [[EC2]] onto Step Functions?
See: [Doc](https://docs.aws.amazon.com/step-functions/latest/dg/bp-activity-pollers.html)
Answer: This can be done via Activity Tasks which enables Activity Worker apps on EC2 or ECS to perform the tasks by polling `GetActivityTask` API on the Step Functions. `SendTaskSuccess` and `SendTaskFailure` status is sent back after the task is completed. Task token is the tracker to ensure coordination. `TimeoutSeconds` is the amount of time after which the task is considered to have failed. `HeartbeatSeconds` is the Keep Task Alive function done via `SendTaskHeartBeat`. Waits can be as long at 1 year.

#Q How should errors be handled ?
See:
Answer: Use `catch` and `retry` in the state machine itself. Retry has various options such as `Error Equals` for matching error types, `Interval Seconds` time to wait before retry, `Max Attempts` and `Backoff Rate`
![[StepFunctions ResultPath.png]]
Fig. Result Path with `$.error` passes on the output with error.

#Q What is the difference between standard and express workflow?
See: [Docs](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-standard-vs-express.html)
Answer: 1 year v 5 minutes. 2000 per second v 100,000 second. Exactly once v either at least once (async) or at most once (sync). No Stepfunction activities support for express.