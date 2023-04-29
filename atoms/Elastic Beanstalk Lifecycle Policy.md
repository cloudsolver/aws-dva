#Q What is the maximum number of application versions in EB and how is it managed.
See: [AWS Doc](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/applications-lifecycle.html)
**Answer:** EB can store at most 1000 application versions. If the versions are not removed, further EB deployments don't work. Option to not to delete the source bundle in S3 to prevent data loss. 
