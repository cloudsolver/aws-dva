### Summary

Accelerate the replication of data into AWS. One-way tasks can move large amounts of data, and meta-data to and from on-prem or other cloud to AWS with NFS, SMB, HDFS, S3 and [[FIPS]] endpoints on a schedule. #AWSService 


### DataSync Details
Accelerate cloud migrations. Move the data and be done.
You can use AWS DataSync to migrate data located on premises, at the edge, or in other clouds to Amazon S3, Amazon EFS, Amazon FSx for Windows File Server, Amazon FSx for Lustre, Amazon FSx for OpenZFS, and Amazon [[FSx]] for NetApp ONTAP. Configure DataSync to make an initial copy of your entire dataset, and schedule subsequent incremental transfers of changing data until the final cut-over from on-premises to AWS.
- Move data directly into [[S3]] Glacier and S3 Glacier Deep Archive.
- Schedule data transfers between:
	- On-Prem and AWS
	- AWS Services
	- AWS and other Cloud
![Agent|350](DataSync%20Agent%20Console.png)
- One agent task can use 10 Gbps. Throttle bandwidth to preserve other workloads #BestPractice 
- Useful if you need the file permissions and metadata are preserved. It copies the data and meta-data. #UseCase 
- Do not use DataSync if you have bandwidth issues, instead opt for [Snowcone](Snow%20Family.md#Snowcone) that comes pre-installed with the DataSync agent. #BestPractice 
![](DataSync%20Agent%20to%20AWS%20DataSync.png)
- Do not use DataSync if you want to create a hybrid architecture, instead use [[Storage Gateway]]
**References**
-  https://aws.amazon.com/datasync/faqs/
- https://tutorialsdojo.com/aws-datasync-vs-storage-gateway/

---
Created on 2023-03-09 16:43