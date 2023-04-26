`aws sts get-session-token` with parameters from MFA `--serial-number arn:aws..` and `--token-code 824093` any number from the device, will return Access Key ID, Access Secret Access Key , and  Session Token. These will need to be entered into the credentials file locally to get access. 

[[AWS SDK]] is built with Python.

**Priority of AWS CLI Credentials Provider Chain**
1. Command Line Options `--region`, `--output` and `--profile` 
2. Environment Variables `AWS_ACCESS_KEY`, `AWS_SECRET_ACCESS_KEY`, and `AWS_SESSION_TOKEN`
3. CLI Credentials file `-aws configure`
4. CLI configuration file `aws configure`
5. Container credentials for ECS Tasks
6. Instance profile credentials - for EC2 Instance profiles

All CLI calls are automatically signed. [[SigV4]] is use to sign the APIs.