# S3 Intro

- S3 is  Object based storage - files store - in buckets.
- Files can be 0 Bytes to 5 TB, and unlimited storage
- S3 is a safe place to store your files.
- S3 is a universal namespace, bucket names should be unique globally.
- https::/s3.amazonaws.com/<bucket-name/<file-name
- HTTP 200 code when upload successful.
- Object consists of :
		- key (Name of the object)
		- Value (This is simply the data and is made up of sequence of bytes)
		- VersionID (inportant for versioning)
		- MetaData (Data about data)
		- Access Control Lists
		- Torrent

### Data Consistency Model
- Read after write consistency for PUTS of new objects (Immediate available)
- Eventual Consistency for overwrite PUTS and DELETES (can take some time to propagate)

### S3 Props
- Built for 99.99% availability for S3 platform.
- Amazon gurantees 99.9% availability
- Amazon guranntees 99.999999999% durability for S3 info (11X9s)
- MFA Delete available for deleting objects.
- Secure your data using Access Control List and Bucket policies

### S3 storage classes

| S3 Standard | S3 - Infrequenct Access | S3 One Zone IA | S3 Intelligent Tiering |
|-------------|-------------------------|----|----|
| 99.99% availability 99.999999999% durability, Stored redundantly across multiple devices in multiple facilities, Designed to sustain the loss of 2 facilies concurrently|99.9% availability 99.999999999% durability, For data that is accessed less frequently but rapid access when needed, Lower fee than S3 but charged a retrieval fee|99.5% availability and 99.999999999% durability, When you wanta lowwer cost option for your IA data but do not require multiple availability zone data resilience|99.9% availability 99.999999999% durability, Designed to optimize cost by moving data to most cost-effective access tier, without performance impact or operational overhead (using ML)|


- S3 Glacier: for like CCTV footage, low cost storage, retrieval time is likely 3-5 hours but configurable to minutes (will cost more though) or hours.
- S3 Glacier Deep Archive: S3 Glaciar Deep Archive is the S3's lowes cost storage where retrival time of 12 hours is acceptable.

### Billing in S3

- Storage - The more you store => The more you will be charged.
- Requests: Number of requests
- Storage management prices (different classes)
- Data Transfer Acceleration
- Transfer Acceleration
- Cross Region Replication Pricing

### Exam Tips 1

- S3 is object based, i.e allows you to upload files.
- Files can be 0B to 5 TB.
- There is unlimied storage.
- Files are stored in Buckets
- S3 is universal namespace (bucket names should ne unique)
- Not suitable to install OS 
- Successful upload: 200 code
- You can turn on MFA delete.
- Key (name of object) - Value (The content of object, made up of a sequence of bytes)
- Version ID, Metadata, Subresources: ACL, Torrents
- Read after write consistency of PUTS of object
- Eventual consistency for overwrite PUTS and DELETES (can take some time to propogate)
- S3 Standard vs S3 IA vs S3-IA One Zone vs S3 Intelligent Tiering vs S3 Glacier, S3 Glacier Deep Archive
- Bucket policy is for the whole bucket vs ACL is where can drill down to the object level


# S3 Encryption

- By default all newly created buckets are private. You can setup access control to your bucket using 1) Bucket Policies 2) ACL
- S3 buckets can be configured to create access logs which log all requests made to S3 bucket. This can be sent to another bucket in another account.

- **Encryption in Transit** is achieved by SSL/TLS 
- **Encryption at Rest** (at server side) is achieved by
- S3 Managed Keys (Amazon manage the keys for you) SSE-S3
- AWS Key Management Keys, Managed Keys - SSE-KMS ( You and Amazon manage the keys)
- Server Side Encryption with Customer provided keys (SSE-C)

** Client side Encryption **: You encrypt the object on your local device and upload it to the S3.

# S3 Versioning

- Stores all versions of an object (including all writes and even if you delete an object)
- Great backup tool
- Once enabled, Versioning can't be disabled, only suspended.
- Integrates with lifecycle rules
- Versioning MFA has delete capability, which use multi-factor authentication, can be used to provide an additional layer of security.
- If you have versioning turned on and making constant changes to large files, the total sie of your bucekts is the sum of all the versions (will increase exponentially)
- Versioning is ON and you delete the file. AWS will put a delete marker (size = 0). File won't be deleted but a delete marker will be added.
- You delete that delete marker and your file will be visible in the bucket. Only way to delete the file is to delete all the individual versions.

# S3 Lifecycle Transition

- Automates moving objects between different storaged tiers	.
- You enter a rule name (eg. TranstionToStandardIA)
- You can filter using prefix / tags for objects you want to transition.
- Can have different transition to different versions of the objects (within the same rule) eg. Current Versions -  TO S3-IA after 30 days and for Previous versions: Transition to S3 Glaciar Deep Archive after 5 days.
- Can also expire the objects (both versions) and clean up the incomplete multipart uploads.

# S3 Cross Region Replication

- Requires Versioning to be enabled on both the source and destination bucket
- Regions must be unique
- Objects that are already upload in the source bucket won't be replicated automatically (Need to do it through command line)
- Can choose destination bucket in different AWS Account
- Takes about a minute to replicate to another region
- Can change the storage class of the bucket to which the content is being replicated (destination bucket)
- Can also change the object ownership to destination bucket owner.
- Need to assign an IAM role while creating replication Rule. One Bucket's access to Another Bucket (IAM Policy)
- Public setting permissions are also replicated.
- If you delete the object in the source bucket (Putting a delete marker) It WON'T put a delete marker in the Destination bucket (Won't be replicateds)
- Even if you delete the latest version, it won't delete the file (or the version) in the destination bucktet

# S3 Transfer Acceleration

- S3 Transfer Accelartion utilises the CloudFront Edge Network to accelerate your uploads to S3.
- Instead of uploading directly to your S3 Bucket, you can use a distinct URL to upload directly to an edge location which will transfer that file to S3.
- You get an endpoint (bucket-name).s3-accelerate.amazonaws.com
- You can transfer data to and from this end-point and it'll be quicker uploads and downloads


# Snowball

- Snowball is a petabyte-scale transport solution that uses secure appliances to transfer large amounts of data into and out of AWS. Using snowball addresses common challenges with large scale data transfer including high network costs, long transfer times, and security concerns. Transferring data with Snowball is simple, fast, secure and can be as little as 1/5th of the cost of high speed internet.

- Snowball Edge - Comes with compute capabilities, it's like having a mini-aws at your home.
- Snowmobile- Exabyte-Scale data transfer 

- Snowball can import to S3 or Export from S3.

# Storage Gateway

- AWS Storage Gateway is a service that connects an on-premise software appliance with cloud-based storage to provide seamless and secure integration between an organization's on premise IT environment and AWS's storage infrastructure.

- The service enables you to securely store data at AWS cloud for scalable and cost-effective storage. 

- Storage Gateway supports either VMWare ESXi or Microsoft Hyper-V. Once you've installed your gateway and associated with your AWS account through the activation process, you can use the AWS management console to create the storage gateway option that is right for you.

- Three Types of storage Gateways:
 1. File Gateway (NFS) - File Gatway (For flat files. stored directly on S3)
 2. Volume Gateway (iSCSI)
 	- Stored Volumes - Entire Dataset is stored on site and is asynchronously backed up to S3.
 	- Cached Volumes - Entire Dataset is stored on S3, and most frequently accessed data is cached on site.
 3. Tape Gatway -  Old Tapes if you're using, you can still migrate to AWS using Gateway Virtual Tape Library. 


# Misc

- Amazon S3 is a simple key-based object store. When you store data, you assign a unique object key that can later be used to retrieve the data.
- If you're unable to delete the bucket. It might be because you aren't the owner of the bucket or the bucket policy denies the DeleteBucket request. (faced this with Elastic Beanstalk bucket)
- To upload a file larger than 80 GB, use the AWS CLI, AWS SDK, or Amazon S3 REST API.
- Multipart upload is a better option for bigger files (AWS recommends any file larger than 100 MB, use multi-part upload)
- When uploading an object through console, In the set permission tab, there is an option to give (R / W) access to other AWS account for that object.
- Query in Place --> Sophisticated queries you can run on your S3 buckets without the need to move data into a separate analytics platform.
- S3 Select, Amazon Athena, and Amazon Redshift Spectrum - these all can be used for querying data in AWS S3.
- S3 Select uses SQL clauses, like SELECT and WHERE, from objects stored in CSV, JSON, or Apache Parquet format.
- Athena is serverless, so there is no infrastructure to setup or manage, and you can start analyzing data immediately.
- While Athena is ideal for quick, ad-hoc querying and integrates with Amazon QuickSight for easy visualization, it can also handle complex analysis, including large joins, window functions, and arrays. 
- Amazon Redshift Spectrum is a feature of Amazon Redshift that enables you to run queries against exabytes of unstructured data in Amazon S3 with no loading or ETL required.
- S3 Transfer Acceleration is a better choice if better throughput is required (it adds additional intelligence between the client and the S3 bucket). However if data is less than 1 GB then consider using Amazon CloudFront.
