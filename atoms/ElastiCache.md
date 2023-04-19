## Summary
A managed Redis or Memcached service. #AWSService 

## ElastiCache Detail
- In-memory databases with high performance and low latency. #performant 
- Reduce load off of databases for read-intensive workloads. #OperationallyExcellent 
- Requires application code changes to use the cache.
### Solution Architecture
- Application will attempt to fetch data from the cache, if `cache miss` it will fetch from RDS, write to cache. #UseCase 
- Sticky session can be eliminated from ALB by using a distributed cache - ensuring stateless infrastructure.
### Technology
- Redis
	- Multi-AZ with Auto-Failover #resilient 
	- Read replicas scale reads #resilient #performant 
	- Data durability using AOF persistence #resilient 
	- Backup and restores.
	- Supports sets and sorted sets.
	- Gaming Leaderboards with guaranteed uniqueness and element ordering, and real time ranking through Redis Sorted Sets. #UseCase 
- MemCached
	- No HA, non-persistent, no backup and restore.
	- Multi-node for partitioning #performant 
### Security
- IAM Authentication for Redis
- IAM policies on ElastiCache are only used for AWS API-level security
#### Redis 
- REDIS AUTH
	- You can set a "password/token" when you create a Redis cluster.
	- This is an extra level of security for your cache.
- Supports SSL in flight encryption. 
- Enable in-transit encryption. 
#### Memcached
- Supports [[SASL]]-based authentication.
### Design Patterns
- Lazy Loading: Cache is loaded on demand.
- Write Through: Data is written to cache first, persistence occurs after.
- Session Store: Store temporary session data in cache with a TTL.
- 
## References

1.