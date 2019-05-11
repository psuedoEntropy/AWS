# Databases Intro

### Relational Databases on AWS:

- SQL Server
- Oracle
- MySQL
- Postgre SQL
- Aurora
- MariaDB

### RDS has two key features:

- MultiAZ - For disaster recovery
- Read Replicas -  For Performance

### Disaster Recovery

- We have two DBs in two different AZs. One Primary and One Secondary.
- For some reason we lost the primary Databases.
- AWS will automatically change the endpoint from Primary to Secondary if Multi-AZ is on.

### Read Replicas

- Wheneever you do a write to the Primary Database. AWS is simultaneously updating (replicating) the read-replica DB.
- This helps balancing in the traffic thereby improving performance.
- However, if the Primary fails, there is no automatic failover to the read replica.
- You'll have to create new URL and update the EC2 instance to point to the new URL (DB).
- Can have 5 copies of Read Replicas.

### Non-Relational Database.

- Collection ==> Table
- Document ==> Row
- Key-Value Pair (JSON) - NoSQL

### Data Warehousing 

- Used for business intelligence (Cognos, Jaspersoft, SQL Server Reporting service, Oracle Hypervision)
- Used to pull in very large and complex data sets. Usually used by management to do queries on data.







# Misc

- After DB is created you can't change the VPC selection

