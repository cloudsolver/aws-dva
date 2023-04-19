## RDS Custom Summary
AWS offers RDS Custom for Microsoft SQL Server and Oracle databases to enable native features, configurations and perform operating system level patches.
## About RDS Custom
*Managed database services for applications that require operating system and database customization.*
- Support MS SQL Server and Oracle only.
- Automates setup, operation, and scaling.
- Access EC2 instance using SSM Session Manager or [SSH](SSH.md).
- #tip Deactivate Automation Mode to perform customization. Take a DB snapshot.

| RDS                        | RDS Custom                  |
| -------------------------- | --------------------------- |
| No access to underlying OS | Access for MySQL and Oracle |
|                            |                             |
|                            |                             |                           |                             |

---
 **References**
1. https://aws.amazon.com/rds/custom/