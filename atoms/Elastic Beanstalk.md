Deploy and scale web applications without thinking about infrastructure provisioning. #AWSService 
[More](https://aws.amazon.com/elasticbeanstalk/)

### Elastic Beanstalk Details
- AWS Elastic Beanstalk uses proven AWS features and services, such as Amazon [[EC2]], Amazon RDS, Elastic Load Balancing, Auto Scaling, Amazon [[S3]], and Amazon [[SNS]], to create an environment that runs your application. The current version of AWS Elastic Beanstalk uses the Amazon Linux AMI or the Windows Server 2019. [faq](https://aws.amazon.com/elasticbeanstalk/faqs/)
- **AWS Elastic Beanstalk** supports the deployment of web applications from Docker containers.
#Q How can you speed up deployments for a website that has static and dynamic content?
Answer: Use Golden AMI for EC2 for static installation parts. Use User Data for dynamic installation parts.

#Q For which of the following scenarios should a solution architect consider using Elastic Beanstalk? (Pick two)
(a) A web application using Amazon RDS
(b) An enterprise Data Warehouse
(c) A long running worker process
(d) Capacity provisioning and load balancing of website
(e) A management task run once on a nightly basis
Answer: Eliminate warehouse because that's best on Redshift. A nightly process sounds more like a batch job. Finally - the long running process might be a fit but it's better with SWF. Look for web application and websites - (a) and (d)
