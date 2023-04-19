## Summary
[EBS Snapshots](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html) allow you to take point-in-time incremental [[Snapshots]] of your volume into S3. EBS Snapshot Archive and Fast Snapshot Restores are offered for different restoration SLAs.

## EBS Snapshot Archive
Move a snapshot to an `archive tier` is 75% cheaper.
Restoration can take some time 24 to 72hrs for restoring the archive.
### Recycle Bin 
A Recycle Bin for EBS Snapshots prevents accidental deletes.
- #Q How can you recover snapshots after an accidental deletion? By setting up rules to retain deleted snapshots.
- Retention from 1 day up to 1 year is possible.

## Fast Snapshot Restore (FSR)
- Force full initialization of snapshot to have no latency on the first use.
- #UseCase . Faster boot times will speed up  VDI environments and allow  Auto Scaling Groups to come online and start processing traffic more quickly, even for large and/or custom AMIs. 
- The trade off is price for performance.

EBS restoration cannot be done to a size smaller, but you can restore to a larger file size.

## References
