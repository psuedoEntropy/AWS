# S3






## Misc

- If you're unable to delete the bucket. It might be because you aren't the owner of the bucket or the bucket policy denies the DeleteBucket request. (faced this with Elastic Beanstalk bucket)
- To upload a file larger than 80 GB, use the AWS CLI, AWS SDK, or Amazon S3 REST API.
- Multipart upload is a better option for bigger files.
- When uploading an object through console, In the set permission tab, there is an option to give (R / W) access to other AWS account for that object.