### Summary
S3 offers Access Points as a mechanism to consolidate and decouple bucket policies from groups of users resulting in a simplified and managed access. It also offers [[Lambda]] Access Point that fronts a lambda function that modifies the data on the fly when a user invokes it - without making copies in S3.

### S3 Access Points Details
- Large shared data sets can be enabled with Access Points e.g. a billing bucket prefix have an access point and permissions given to [[IAM]] groups to the access point.
- You can create Access Points for access to buckets within a [[VPC]]. An [[SCP]] can firewall your [[S3]] buckets behind the Access Points.
- You can give it any name you want because it is in the scope of the VPC.
- Configure to restrict access  to a particular VPC.

### S3 Object Lambda Access Point
An Object Lambda access point is associated with exactly one standard access point and thus one Amazon S3 bucket
![[lambda_access_point_arch.png|512]]
Fig. The Redacting Lambda Function as well as the Enriching Lambda Function will sit between the S3 Object Lambda Access Point and the Supporting S3 Access Point. 
- Data transformation of formats e.g. JSON to XML.
- Watermarking images with personalization or redacting documents e.g. PII.
### References

1. [S3 Access Points](https://aws.amazon.com/s3/features/access-points/)
2. [S3 Lambda Access Point](https://docs.aws.amazon.com/AmazonS3/latest/userguide/olap-create.html)