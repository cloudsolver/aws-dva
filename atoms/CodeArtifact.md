#Q What is the purpose of Code Artifact?
See:
Answer: 
![[CodeArtifact Architecture.png]]

---

#Q A new security vulnerability was just discovered, and a patch is out. How do you track your dependencies down and patch your applications?
See: 
Answer: Recently, log4j was vulnerable and there was a mad rush to find applications and update the dependencies. The business value for investing in CI-CD that is well-architected can respond in the following way:
![[CodeArtifact-CodePipeline EventBridge Architecture.png]]

---

#Q How is a repository given access to another user in a different AWS account?
**Answer**: Using a Resource Policy, a user from another account can be given access. It's a resource based policy.

---

#Q How are repository chains set up and what are the limits?
**Answer**: Each repository can have up to 10 upstream repository. Each repository can have a maximum of one external connection e.g. npm. The dependency search chain can be optimized to look through upstreams and then outbound.
![[CodeArtifact Repository Retention.png | 256]]
Fig. NPM Repository Chaining

---
#Q How should duplication of storage of the artifacts be managed ?
Answer: Use Domains. With CodeArtifact Domains, shared storage for artifacts is set up that way only references/pointer from the artifacts are pointing to the shared storage env.

![[CodeArtifact Domain Architecture.png|256]]