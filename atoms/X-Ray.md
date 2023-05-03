#Q How does X-Ray work to provide tracing?
See: [Developer Guide](https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html)
**Answer**: Applications need to be instrumented with the X-Ray SDK that supports various languages. Trace data in JSON-snippet is sent to the X-Ray daemon over UDP. [[EC2]] instances must have the daemon installed and running and [[IAM]] role has proper permissions e.g. `AWSXRayDaemonWriteAccess` includes permission to upload traces. For Lambda, ensure it has an IAM execution role with proper policy.
![[X-Ray Architecture.png]]
Fig. X-Ray Architecture
