An #AWSService that supports [[GraphQL]]. Retrieve data in real-time using [[WebSockets]] and [[MQTT]] over [[WebSockets]].

#Q How does AppSync integrate with DynamoDB?
See: [FAQ](https://aws.amazon.com/appsync/faqs/)
Answer: It can import the schema and be a resolver.

#Q What are authorization mechanisms?
See:
Answer: KEY, AWS_IAM, OPENID_CONNECT and AMAZON_COGNITO_USERPOOLS. Use [[CloudFront]] for encryption in transit.

#Q What should be used to allow multiple users to synchronize and collaborate shared data in real time.
Answer: AppSync supports it. However,  for cross-device syncing of user profile still use AppSync because [[Cognito Sync]] is now deprecated.