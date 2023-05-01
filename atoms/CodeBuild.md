#Q What does CodeBuild do?
See: [CodeBuild User Guide](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html)
Answer:  Fully managed Continuous Integration service (like Jenkins). It uses `buildspec.yml` to specify environment in `env`, including parameter-store, secrets-manager. `phases`, `artifacts`, and `cache`. By default, CodeBuild runs all build commands as the root user.
![[CodeBuild Architecture.png]]

#Q How can you troubleshoot?
See: [Troubleshooting](https://docs.aws.amazon.com/codebuild/latest/userguide/troubleshooting.html)
Answer: You can install locally for troubleshooting within a local Docker runtime using the CodeBuild Agent.