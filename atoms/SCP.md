### Service Control Policies [[SCP]]
SCP can only filter, they never add permissions. Only deny propagates down.

Policies at the org root are inherited by children accounts. Policies at the [[OU]] are inherited by its children.

To apply the restrictions across multiple member accounts you must use a Service Control Policy (SCP) in the AWS [[Organization]]. The way you would do this is to create a **deny** rule that applies to anything that does not equal the specific instance type you want to allow.