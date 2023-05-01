#Q How are CodeCommit repositories secured?
See: [User Guide](https://docs.aws.amazon.com/codecommit/latest/userguide/data-protection.html)
**Answer:** CodeCommit repositories are automatically encrypted at rest. No customer action is required. CodeCommit also encrypts repository data in transit. You can use either the HTTPS protocol, the SSH protocol, or both with CodeCommit repositories. TLS 1.3 is recommended. [[IAM]] users with least privilege is recommended with MFA.
Works with [[CodePipeline]].