Deploy and scale web applications without thinking about infrastructure provisioning. #AWSService 
[More](https://aws.amazon.com/elasticbeanstalk/)

### Elastic Beanstalk Details
- AWS Elastic Beanstalk uses proven AWS features and services, such as Amazon [[EC2]], Amazon RDS, Elastic Load Balancing, Auto Scaling, Amazon [[S3]], and Amazon [[SNS]], to create an environment that runs your application. The current version of AWS Elastic Beanstalk uses the Amazon Linux AMI or the Windows Server 2019. [faq](https://aws.amazon.com/elasticbeanstalk/faqs/)
- **AWS Elastic Beanstalk** supports the deployment of web applications from Docker containers.
#Q How can you speed up deployments for a website that has static and dynamic content?
**Answer**: Use Golden AMI for EC2 for static installation parts. Use User Data for dynamic installation parts.

### Deployment options

See [[Elastic Beanstalk Deployment Policies]]

### EB Lifecycle Policy
See [[Elastic Beanstalk Lifecycle Policy]]

### EB Extensions and Advanced Features
#Q How is the EB environment extended?
See:[AWS Doc](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html)
Answer: in the root of the source code `.ebextensions` directory should contain `anynamehere.config` files in YAML or JSON format. You can add [[RDS]], [[ElastiCache]], [[DynamoDB]] resources. However, these resources will get deleted if the environment is every deleted.

#Q How do you ensure RDS is decoupled from EB environment?
See: [AWS Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.managing.db.html)
**Answer**: Create a EB environment. Then prevent deletion of the RDS instance. Create a new environment (not clone) without RDS, instead use the RDS connection string from the previous environment. As an alternative to using a decoupled database that Elastic Beanstalk created, you can also create a database instance outside of your Elastic Beanstalk environment. Both options result in a database instance that's external to your Elastic Beanstalk environment and will require additional security group and connection string configuration.

#Q How do you support HTTPS for web applications?
Answer: Use [[ACM]] and [[ALB]] and create a rule to redirect HTTP to HTTPS

#Q How can you create a custom platform? Any why would you need to?
Answer: If Docker is not possible. Create your own platform with `Platform.yaml` file. Build it using Packer software (open source) to create AMI.

#Q How do you migrate an EB env from on AWS account to AWS another?
See: [Blog](https://repost.aws/knowledge-center/elastic-beanstalk-migration-accounts)
**Answer**: You must use [saved configurations](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environment-configuration-savedconfig.html) to migrate an Elastic Beanstalk environment between AWS accounts.
### EB with Docker

#Q What is the architecture for running a single instance and multi-instance Docker containers ?
See:
**Answer**: EB will simply run Docker directly on [[EC2]]. For multi-container set up it does use [[ECS]] instead. Requires a `Dockerrun.aws.json` to generate the ECS task definition and use the EC2 Deployment Type.

### Quiz
#Q For which of the following scenarios should a solution architect consider using Elastic Beanstalk? (Pick two)
(a) A web application using Amazon RDS
(b) An enterprise Data Warehouse
(c) A long running worker process
(d) Capacity provisioning and load balancing of website
(e) A management task run once on a nightly basis
**Answer**: Eliminate warehouse because that's best on Redshift. A nightly process sounds more like a batch job. Finally - the long running process might be a fit but it's better with SWF. Look for web application and websites - (a) and (d)
