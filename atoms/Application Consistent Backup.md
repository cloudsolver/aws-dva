## Summary
Data is flushed to disk, the application is suspended, then a backup is taken.
## Application Consistent Backup Details
Transactions, and pending application transactions are captured in the backup. The [[ACID]] properties of a transaction are preserved. This is usually done by either rolling back transaction or forcing pending transactions to disk before a backup.

Application-consistent copies are made after making sure that current application operations are temporarily ceased (quiesced/stunned) and any data in memory is flushed to disk.

## References
1. https://www.computerweekly.com/feature/Storage-101-Crash-consistent-vs-application-consistent-snapshots
2. https://www.youtube.com/watch?v=jzm5-y-xa1M&ab_channel=Carbonite