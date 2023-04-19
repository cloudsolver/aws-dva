### Summary of Redshift
Amazon Redshift uses SQL to analyze structured and semi-structured data across data warehouses, operational databases, and data lakes, using AWS-designed hardware and machine learning to deliver the best price performance at any scale. #AWSService 
### Redshift Details
* Data warehouse: data storage solution with historical data from disparate sources.
* Business intelligence, querying and business intelligence.
* Handles exabyte-scale data. OLAP implementation based on PostgreSQL engine.
* Loading data into Redshift. Large inserts are much better. #BestPractice 
#UseCase 
	Data consolidation. Run a database when it doesn't require CRUD.
	Analytics - allows querying to gain business insights.
	Faster queries, data aggregation due to ability to index as compared to [[Athena]].

#Q How to isolate from public Internet?
Enhanced VPC Routing allows you to use Amazon VPC Endpoints and VPC security groups to control access to your Redshift clusters. With Enhanced VPC Routing, all COPY and UNLOAD traffic is routed through the Amazon VPC and can be isolated from the public internet. This can help improve security and compliance, and reduce the risk of data exfiltration or unauthorized access. #secure 

#Q How do you link Redshift to S3 without loading it into Redshift?
Using Amazon Redshift Spectrum, you can efficiently query and retrieve structured and semistructured data from files in Amazon S3 without having to load the data into Amazon Redshift tables.
![[Redshift Spectrum S3 Architecture.png]]
Fig. Redshift with Spectrum
> Default Standard Internet Routing
By default, Amazon Redshift uses standard Internet routing for COPY and UNLOAD traffic, which can bypass your VPC and traverse the public internet. Enhanced VPC Routing ensures that all traffic between your cluster and data repositories stays within your VPC, providing an additional layer of protection and control. #secure 


 #Q How to prepare Redshift for [[DR]] ?
 Use automated snapshots to another region. 
There is a multi-AZ option now available too. #resilient 
![[redshift-cross-region-restore-solution.png|256]]

#Q How can Redshift run a few quick queries against data in S3 in a cost-effective way? #CostOptimized 
(a) Use Redshift Direct Access
(b) Use Redshift Spectrum
(c) Compress S3 into Redshift
(d) Use Amazon Workload Management to run SQL Queries directly
Answer: You need to know the Redshift product features from the faq. Spectrum allows you to execute queries into your datalake inside S3. [FAQ](https://aws.amazon.com/redshift/faqs/)
#### References for Redshift
1. [RedShift](https://aws.amazon.com/redshift/)

---
Created on 2023-03-14 16:55
