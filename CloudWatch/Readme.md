# CloudWatch 

- Cloud Watch monitor performance. 
- CloudTrail monitors API calls logs.

## CloudWatch monitor

- Cloud watch can monitor things like:
- Compute (EC2 Instances, Autoscaling groups, Elastic Load Balances, Route53 Healthchecks)
- Storage & Content Delivery (EBS Volumes, Storage Gateways, CloudFront)

## Host Level Metrics Consists of:

- CPU
- Network
- Disk
- Status Check

## AWS CloudTrail - like a CCTV camera.

- You create a bucket
- You fired up an EC2 Instance
- You enabled detailed cloudwatch on it
- You made API call to change DB Parameters
- You made API call to modify snapshot
- Basically anything that you do through Management calls or API calls;
- You can identify which users and accounts called AWS, the source IP addresses from which these calls were made, and when the calls occured.
- CloudTrail is all about auditing.

# Exam Tips

- Standard monitoring is 5 minutes
- Detailed Monitoring is 1 minute
- Dashboards - You can create Dashboards to see what is happening with your AWS environment.
- Alarms -  Allows you to set Alarms that notify you when a particular thresholds are hit.
- Events -  Cloudwatch events helps you to respond to state changes in AWS resources.
- Logs - CloudWatch logs helps you to aggregate, monitor, and store logs
- CloudWatch vs CloudTrail