Elastic Map Reduce can easily run and scale open source big data platforms with full access to the underlying operating system. This service runs on [[EC2]] as well as [[ECR]] and [[Fargate]] #AWSService 

### Details
- Process large amounts of data via map reduce.
- Analyze data using Hadoop and Apache Spark.
- Run and manage your workloads with the EMR, API, SDK or CLI and orchestrate them using Amazon Managed Workflows for Apache Airflow (MWAA) or AWS [[Step Functions]]. For an interactive experience you can use EMR Studio or SageMaker Studio.
 #Usecase: Perform big data analytics, build scalable data pipelines, process real-time data streams, accelerate data science and ML adoption.
- Amazon EMR on [[EC2]] and [[KMS]] allow customizing operating system images.
- Master Node: Manage health of the cluster.
- Core Node: Run tasks and store data.
- Task Node: Just to run tasks - usually Spot.
- Purchasing Options: On-demands, Reserved, Spot.

**References**
[EMR Home Page](https://aws.amazon.com/emr/) Map Reduce