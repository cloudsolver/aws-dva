#Q What are the steps for making CodeDeploy work?
Answer: CodeDeploy Agent polls AWS CodeDeploy and when it has a signal, it will pull code and `appspec.yml` to execute all instructions contained within it.
![[CodeDeploy Architecture.png|384]]
Fig. CodeDeploy Architecture

---

#Q What are the primary components of CodeDeploy?

| Name                 | Description                                                                               |
| -------------------- | ----------------------------------------------------------------------------------------- |
| Application          | Unique name, functions as a container                                                     |
| Compute Platform     | EC2, On-Prem, Lambda, ECS                                                                 |
| Deployment Config    | Set of deployment rules for success or failure e.g. min number of healthy instances       |
| Deployment Group     | Group of tagged EC2 instances |
| Deployment Type      | Method used to deploy the application to a Deployment Group eg. In-place, Blue/Green      |
| IAM Instance Profile | EC2 instances the permissions to access S3 or GitHub                                      |
| Service Role         | IAM Role for CodeDeploy to perform operations on EC2 instances, ASGs, ELBs...             |
| Target Revision      | The most recent revision that you want to deploy to a Deployment Group                    |
Table. CodeDeploy Components

---

#Q What are the CodeDeploy Deployment Configurations?
Answer:  
1. One at a time: One EC2 instance at a time, if one instance fails, then deployment stops
2. Half at a Time: 50%
3. All At Once; Good for dev env as it's the fastest
4. Custom: 25% etc.
---

#Q How are Failures handled?
Answer: EC2 instances stay in the "failed" state. New deployments will first be deployed to failed instances. 
#Q How are Rollback handled?
Answer: In order to rollback, redeploy old deployment or enable rollback or failure.