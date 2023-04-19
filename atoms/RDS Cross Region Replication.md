## Summary
RDS offers cross-region replicas to reduce read latency across Regions, enable cross-Region database migration and low RPO/RTO DR. This is done via Write-Ahead Log (WAL) streaming.

## About

During the creation of a cross-Region replica, RDS will:
- take a snapshot of the source instance.
* Configure replication slot streaming between source and replica.
* Start WAL streaming.
![500](https://d2908q01vomqb2.cloudfront.net/887309d048beef83ad3eabf2a79a64a389ab1c9f/2020/04/10/Best-practices-cross-Region-read-replicas-A.png)
## References
- https://aws.amazon.com/blogs/database/best-practices-for-amazon-rds-for-postgresql-cross-region-read-replicas/
- https://www.postgresql.org/docs/current/app-pgreceivewal.html