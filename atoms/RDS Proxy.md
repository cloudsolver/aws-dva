## RDS Proxy

- Enforce IAM Authentication for DB, and securely store credentials in AWS Secrets Manager.
- Pool and share DB connections established with the database.
- Improve database efficiency by reducing stress on the RDS Database instance by minimizing open connections, timeout and optimize. #OperationallyExcellent
- Serverless, autoscaling and highly available (multi-AZ).
- Reduced RDS and [[Aurora]] failover time by up to 66%.
- Enforce [[IAM]] Auth for DB, and securely store credentials in AWS Secrets Manager. #secure 
- Never publicly available.You cannot connect from the Internet - only within [[VPC]]. #secure
- [[Lambda]] functions can connect to RDS Proxy and will not overwhelm the database. #UseCase 