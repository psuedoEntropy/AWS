# S3

## Intro

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
- AMazon gurantees 99.9% availability
- Amazon guranntees 99.999999999% durability for S3 info (11X9s)
- MFA Delete available for deleting objects.
- Secure your data using Access Control List and Bucket policies

### S3 storage classes

| S3 Standard | S3 - Infrequenct Access | S3 | S3 |
|-------------|-------------------------|----|----|
| 99.99% availability 99.999999999% durability
Stored redundantly across multiple devices in multiple facilities
Designed to sustain the loss of 2 facilies concurrently|99.9% availability 99.999999999% durability
 For data that is accessed less frequently but rapid access when needed
 Lower fee than S3 but charged a retrieval fee| X | X|











## Misc

- Amazon S3 is a simple key-based object store. When you store data, you assign a unique object key that can later be used to retrieve the data.
- If you're unable to delete the bucket. It might be because you aren't the owner of the bucket or the bucket policy denies the DeleteBucket request. (faced this with Elastic Beanstalk bucket)
- To upload a file larger than 80 GB, use the AWS CLI, AWS SDK, or Amazon S3 REST API.
- Multipart upload is a better option for bigger files (AWS recommends any file larger than 100 MB, use multi-part upload)
- When uploading an object through console, In the set permission tab, there is an option to give (R / W) access to other AWS account for that object.