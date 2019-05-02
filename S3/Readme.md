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

** Encryption in Transit ** is achieved by SSL/TLS 
** Encryption at Rest ** (at server side) is achieved by
- S3 Managed Keys (Amazon manage the keys for you) SSE-S3
- AWS Key Management Keys, Managed Keys - SSE-KMS ( You and Amazon manage the keys)
- Server Side Encryption with Customer provided keys (SSE-C)

** Client side Encryption **: You encrypt the object on your local device and upload it to the S3.




## Misc

- Amazon S3 is a simple key-based object store. When you store data, you assign a unique object key that can later be used to retrieve the data.
- If you're unable to delete the bucket. It might be because you aren't the owner of the bucket or the bucket policy denies the DeleteBucket request. (faced this with Elastic Beanstalk bucket)
- To upload a file larger than 80 GB, use the AWS CLI, AWS SDK, or Amazon S3 REST API.
- Multipart upload is a better option for bigger files (AWS recommends any file larger than 100 MB, use multi-part upload)
- When uploading an object through console, In the set permission tab, there is an option to give (R / W) access to other AWS account for that object.