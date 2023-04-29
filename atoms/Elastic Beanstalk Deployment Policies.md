#Q What are the deployment options for updating applications?
See: [AWS docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.rolling-version-deploy.html) outlines the deployment policies.
**Answer**:   _All at once_, _Rolling_, _Rolling with additional batch_, _Immutable_, and _Traffic splitting_ and _Blue/Green_ and [[A-B Testing Blue-Green Deployment| blue/green]] deployment option is not our of the box, however it can be done with manual workaround. Create a new environment and change the CNAME for instant traffic.
You can manually swap URLs.

| Method                        | Risk                        | Deploy Time | App Downtime   | No DNS Change | Rollback                                    | Code Deployment            |
| ----------------------------- | --------------------------- | ----------- | -------------- | ------------- | ------------------------------------------- | -------------------------- |
| All At Once                   | There is downtime           | Fastest     | Planned outage | True          | Manual                                      | Existing Instance          |
| Rolling                       | Single Batch out of service | Fast        | None           | True          | Manual                                      | Existing Instances         |
| Rolling with Additional Batch | Minimal                     | Slow        | None           | True          | Manual                                      | New and Existing Instances |
| Immutable                     | Minimal                     | Slowest     | None           | True          | Terminate New Instances                     | New Instances              |
| Traffic Splitting             | Percentage of new traffic   | Slowest     | None           | True          | Reroute Traffic and terminate new instances | New Instances              |
| Blue/Green                    | Minimal                     | Slowest     | None           | False         | New Instances                                            |                            |
Table. Comparison of Deployment Policies