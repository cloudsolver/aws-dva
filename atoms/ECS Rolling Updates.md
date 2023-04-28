The service started must use the *rolling update* ECS deployment type.
ECS Scheduler replaces currently running tasks wit new tasks.
Deployment configuration `minimumHealthyPercent` and `maximumHealthyPercent` values are defined when service is created.
![[ECS Rolling Update Console.png]]
Fig. ECS Rolling Update Console

Amazon ECS controls the **rolling update** deployment type. This deployment type involves the service scheduler replacing the current running version of the container with the latest version. You can control the number of tasks that the service scheduler adds or removes from the service during a rolling update by adjusting the minimum and maximum percent of healthy tasks allowed during a service deployment.