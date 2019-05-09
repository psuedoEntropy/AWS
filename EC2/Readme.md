# EC2 Intro

- Amazon Elastic Compute Cloud (EC2) is a web service that provides resizable compute capacity in the cloud.
- Amazon EC2 reduces the time required to obtain and boot new servers in minutes.

### EC2 Pricing Models

- **On Demand**: Allows you to pay a fixed rate by the hour (or by the second) with no commitment.
- **Reserved**: Provides you with the capacity reservation, and offer a significant discount on the hourly charge for an instance. Contract terms are 1 year or 3 Years.
- **Spot Instances**: Enables you to bid whatever price you want for instance capacity, providing for even greater savings if your application have flexible start and end times.
- **Dedicated Hosts**: Physical EC2 servers dedicated for your use. Dedicated hosts can help you reduce costs by allowing you to use your existing 	server-bound software licenses.

### On Demand Pricing is useful for:

- Users that want the low cost and flexibility of Amazon EC2 without any up-front payment or long-term commitment.
- Applications with short term, spiky or unpredictable workloads that cannot be interrupted.
- Applications being developed or tested on Amazon EC2 for the first time. 

### Reserved Pricing is useful for:

- Applications wit steady state or predicatable usage.
- Applications that require reserved capacity
- Users able to make upfront payments to reduce their total computing costs even further.

**Types**:
- Standard Reserve Instances: offer up to 75% off on demand instances. The more you pay up front the longer the contract, the greater the discount. (Can't convert t2.micro to r4.large)
- Convertible Reserved Instances: These offere 54% off on demand capability to change the attributes of the Reserved Instances of equal or greater value.
- Scheduled Reserved Instances: These are available to launch within the time windows you reserve. This option allows you to match your capacity reservation to a predictable recurring schedule that only reuires a fraction of a day, week, or a month.

### Spot Pricing is used for:

- Applications that have flexible start and end times.
- Appications that are only feasible at very low compute prices.
- Users with urgent computing needs for large amounts of additional capacity.	
- If the spot instance is terminated by Amazon EC2, you'll not be charged partial hour of usage. However, if you terminate the instance yourself, you will be charged for any hour in which the instance ran. 

### Dedicated Hosts pricing is useful for:

- Useful for regulatory reuirements that may not support multi-tenant virtulization.
- Great for licensing which does not support multi-tenancy or cloud deplyoments.
- Can be purchased as a reservation for up to 70% off the on-demand price.

### Fight Dr McPxz AU
|F |I |G |H |T |D |R |M |C |P |X |Z |A |U |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
|FGPA|IOPS|Graphics|High Disk Throughput|Cheap General Purpose|Density|RAM|Main choice for GP|Compute|Graphics|Extreme Memory|Extreme memory and CPU|Arm-based workloads|Bare metal|

## Exam Tips 1

- Termination protection is turned off by default, you must turn it on.
- On an EBS-backed instance, the *default action is for the root EBS volume to be deleted* when the instance is terminated.
- EBS Root volumes of your DEFAULT AMI's can't be encrypted.
- Additional volumes can be encryped.


# Security Groups

- When creating a security group, everything (all inbound) is blocked by default, you can allow Ports ever a CIDR range but can't "Deny".


- All outbound traffic is allowed. Security groups are *STATEFUL*
- If you create an inbound rule allowig traffic in, that traffic is automatically allowed back out again.
- Changes to security groups take effect immediately.
- You can't block specific IP addresses using SG, instead we use Network Access Control Lists( NACLs).
- You can specify rule, but can't deny rule.
- You can have any number of EC2 instances within a security group.
- You can also attach more than one security group to an EC2 instance.

# EBS

- Amazon Elastic Block Store (EBS) is just a virtual hard-disk on the cloud. 
- It's not object-based like S3; It's Block-based (as you can see by the name)
- Block-based means you can install OS on it and softwares as well.
- EBS Volume is automatically replicated within it's Availability Zone to protect from Component failure.
- Offers High-availability and durability.

## 5 Different Types of EBS

### General Purpose SSD

- Peformance for Wide Variety of workloads
- Most work loads
- API Name: gp2
- Max IOPS: 16,000

### Provisioned IOPS (SSD)

- Highest performance SSD
- Database workloads
- API Name: io1
- Max IOPS: 64,000

### Throughput optimized HDD

- Low cost HDD Volume designed for throughput intensive workloads
- Designed for frequently accessed workloads
- Big data and data warehousing
- API Name: st1
- Max IOPS: 500

### Cold HDD

- Lowest cost HDD volume
- Designed for less frequently accessed workloads
- File servers
- API Name: sc1
- Max IOPS: 250

### EBS Magnetic

- Previous generation HDD
- Infrequent accessed data workloads
- Max IOPS: 40-200










# Misc

- Root Device volumes are not encrypted by default. When launching an instance the first team, the root device can't be encrypted at any cost.
- However you can later encrypt it using snapshots and copying image.


