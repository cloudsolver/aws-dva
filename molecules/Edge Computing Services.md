### Compare Lambda@Edge versus CloudFront Functions
There are various differences between choosing [[Lambda#Lambda@Edge]] or [[CloudFront#CloudFront Functions]]


|                      | CloudFront Functions             | Lambda@Edge                     |
| -------------------- | -------------------------------- | ------------------------------- |
| Access Internet      | No                               | Yes                             |
| Access Filesystem    | No                               | Yes                             |
| Scale                | Millions per sec                 | Thousands per sec               |
| Supports JavaScript  | Yes                              | Yes                             |
| Read Request Body    | No                               | Yes                             |
| Timeout              | 5 sec (client) - 30 sec (origin) | 1 ms                            |
| Memory               | 2 MB                             | 128 MB - 10 GB                  |
| Package              | 50 KB                            | 1 MB - 50 MB                    |
| Access VPC Resources | No                               | No                              |
| Supports Env Vars    | No                               | No                              |
| Supports [[DLQ]]     | No                               | No                              |
| Pricing              | Free Tier Eligible               | 6x cost vs CloudFront Functions |

Table. CloudFront Functions versus Lambda@Edge