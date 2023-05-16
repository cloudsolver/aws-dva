### Authentication
- Short-lived credentials can be created with `AWSAuthenticationPlugin` with IAM.
- **IAM DB Authentication** - manage your database user credentials through AWS IAM users and roles.
#Q How do you use the profile credentials specific to your EC2 instance to access your database, instead of a password?
	-Use IAM DB Authentication
### At-rest encryption
  - Database master and replicas encryption using AWS [[KMS]] - must be defined at launch time.
  - If master is not encrypted - the replicas cannot be encrypted.
  - DB snapshot, restore as encrypted.
#UseCase Enable encryption for the database without incurring any data loss:
Encrypt: take a snapshot, encrypt a copy of the snapshot and restore the snapshot to a new RDS DB instance
Sync Data: Use [[DMS]] to sync data to the new RDS DB instance from the old RDS instance.
#Q What is TDE?
In the context of Amazon RDS (Relational Database Service), TDE stands for Transparent Data Encryption. TDE is a feature provided by Amazon RDS that allows you to encrypt data at rest in your database instances. It helps protect sensitive data stored in your RDS databases by automatically encrypting the data files, including backups, snapshots, and replicas.

### In-Flight Encryption
- TLS-ready by default. 
- Use AWS TLS root certificate client-side.
- #UseCase Force all connections to your DB instance to use SSL by setting the `rds.force_ssl` parameter to true. Once done, reboot your DB instance.
- #UseCase Enforce SSL on MySQL DB Instance: Execute `REQUIRE SSL` on all DB users.
#UseCase Amazon RDS creates an SSL certificate and installs the certificate on the DB instance when Amazon RDS provisions the instance. These certificates are signed by a certificate authority. The SSL certificate includes the DB instance endpoint as the Common Name (CN) for the SSL certificate to guard against spoofing attacks.
### Security Groups
- Control network access to RDS/Aurora DB.