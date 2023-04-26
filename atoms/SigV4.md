AWS API calls must be signed with SigV4 *except S3 public buckets*

### HTTP Header
Authorization: AWS4-HMAC-SHA256 Credential=
SignedHeaders=

### Query String e.g. S3 pre-signed url
X-Amz-Algorithm=
X-Amz-Credential=
X-Amz-Date=
X-Amz-Signature=

The [[STS]] generated temporary credentials are automatically expired and rotated. #secure 

