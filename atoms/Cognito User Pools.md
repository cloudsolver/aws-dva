- Create and managing a user directory for your application, providing secure user authentication and authorization features out-of-the-box
- User directory service. Sign-up and sign in to provide authentication for app users.
- Move authentication capability from the backend of your application to Cognito.
- Serverless database for users - supports for MFA, email verification, third party auth e.g. Google auth.
- Custom Domains must use [[ACM]] from the us-east-1 region.
- CUP issues JWT Tokens (Base64) = header, payload and signature. The signature can validate the payload integrity.
- [[ALB#ALB Authentication]] can be used to Authenticate users.
![[User Pool Auth Architecture.png|512]]
Fig. User Auth, Tokenization,  and Integration with [[API Gateway]] and [[ELB#ALB]]

--- 

#Q How are user pool workflows customized?
See: [Docs](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-identity-pools-working-with-aws-lambda-triggers.html)
**Answer**: Lambda triggers can be assigned to your user pool. Amazon Cognito interrupts its default flow to request information from your function. Examples: Pre-Signup, Post Confirmation, Pre and Post AuthN.

#### QUIZ
#Q You have a social media web/mobile application that uses API Gateway, Lambda, DynamoDB, and Cognito. You have been tasked to synchronize user profile data across mobile devices and the web without requiring your own backend. Which of the following helps you achieve this?
(a) Cognito Sync
(b) Cognito User Pool
(c) Cognito Identity Pool
(d) App Sync
See: [Docs](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-sync.html)
Answer: The current recommendation is to use App Sync otherwise if you're already a user - it is Cognito Sync.

#Q You would like to authenticate your users against Facebook before they are able to make requests to your API hosted by API Gateway. What should you use to make a seamless authentication integration?
(a) Cognito User Pool
(b) Cognito Federated Identity Pool
(c) Cognito with Lambda Authorizer
(d) Cognito Sync
Answer: The answer 

