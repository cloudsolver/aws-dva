### Summary
S3 can host static websites directly in buckets. Provides fine-grained CORS control and private pre-signed URLs.
## S3 Website Details
* URL pattern:  `http://bucketname.s3-website.awsregion.amazonaws.com`
	* `s3-website-awsregion` can be hyphenated in certain regions.
	* `http://spectrumvending.com.s3-website-us-east-1.amazonaws.com` is hosted on S3.
* `403 Forbidden` - make sure policy allows pubic reads.
* S3 Bucket must be the same name as the registered domain name e.g. S3 bucket name for https://rohitsood.com must be `rohitsood.com`

### S3 CORS
Cross-Origin Resource Sharing is supported by S3 Website hosting feature under permissions.

### S3 Pre-Signed URL
Often S3 Pre-signed URLs are used to prevent public access to objects while providing temporary access to an object for upload or download.
- Only allow logged-in users access to the files.
- Allow a user a precise location to upload a file.
- Dynamically generate a signed-url to give users access.


**References**

1. [S3 Web Hosting](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
2.  [S3 CORS](https://docs.aws.amazon.com/AmazonS3/latest/userguide/cors.html)
