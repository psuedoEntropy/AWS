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
- Unlike RDB, they don't have to have consistencies
- DynamoDB - Amazon's NoSQL database

### Data Warehousing 

- Used for business intelligence (Cognos, Jaspersoft, SQL Server Reporting service, Oracle Hypervision)
- Used to pull in very large and complex data sets. Usually used by management to do queries on data.

- *OLTP*: Pull up a row (rows) from a Database. (Normal Queries)
- *OLAP*: Calculation on Data and give you the final result. (Complicated queries)

- Data Warehousing databases use different type of architecture both from a database persepctive and infrastructure layer.

- Amazon's Data Warehouse Solution is called Redshit

### ElastiCache

- ElastiCache is a web service that makes it easy to deploy, operate, and scale an in-memory cache in the cloud. The service improves the performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches, instead of relying entirely on slower disk based databases. - Memcached & Redis









# Misc

- After DB is created you can't change the VPC selection
- You can now specify the DB Instance Performance Type: 3 different types:
- ***Standard***: General purpose instances provide a balance of compute, memory, and networking resources, and can be used for a variety of workloads.
- ***Memory Optimized***: Memory optimized instances are designed to deliver fast performance for workloads that process large data sets in memory.
- ***Burstable***: Burastable instances are designed to provide a baseline level of CPU performance with the ability to burst to a higher level when required by your workload.

