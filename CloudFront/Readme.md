# CloudFront Intro

- It is a content delivery network (CDN). A CDN is a system of a distributed servers (network) that deliver webpages and other web content to a user based on the geographical locations of the user, the origin of the webpage and a content delivery server.

- **Edge Location** -  This is a location where content will be cached. This is separate to an AWS Region/AZ.
- **Origin** -  This is the origin of all the files that the CDN will distibute. This can be S3 Bucket, EC2 Instance, ELB, or Route53.
- **Distribution** - This is the name given to the CDN which consists of collection of Edge Location.

1st user will try to find a page, if it's not on the edge location, it will download it from the origin and save it on the edge location for the Time To Live.
2nd user queries that page, that page will load fast, because it has been loaded on the Edge location.

- Web Distributions: Typically used for websites.
- RTMP: Used for Media Streaming (Adbobe Flash Media)

- Edge Locations are not just read-only. You can write to the edge locations as well (put object on them)
- You can clear cached object but you will be charged for it.

