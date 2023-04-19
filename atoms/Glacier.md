### Glacier 
Low cost option for archival and backup. Cost for object retrieval. It is almost impossible to load data directly into Amazon S3 Glacier without using a lifecycle policy. Possible to directly push to Glacier via [[Storage Gateway]] Tape Volumes.

### Instant Retrieval
- Millisecond retrieval, minimum storage duration 90 days.
- Quarterly instantaneous retrieval. #UseCase 

### Flexible Retrieval
- Expedited (1-5 mins)
- Standard (3-5 hrs)
- Bulk (5-12 hrs): Free
- Minimum 90 days storage.
### Deep Archive
- Minimum 180 days, retrieval 12 hours

### Quiz
#Q A user is trying to create a vault in AWS Glacier. The user want to enable notifications. In which of the below mentioned options can the user enable the notifications from the AWS console?
(a) Glacier does not support the AWS console.
(b) Archival upload complete
(c) Vault upload job complete
(d) Vault Inventory Retrieval Job Complete
Answer: You can use the AWS Console to configure Vault Notifications (See this)[https://docs.aws.amazon.com/amazonglacier/latest/dev/configuring-notifications-console.html]. You cannot upload directly to Glacier - therefore options (b) and (c) are invalid. S3 Glacier defines events specifically related to job completion (`ArchiveRetrievalCompleted`, `InventoryRetrievalCompleted`).

