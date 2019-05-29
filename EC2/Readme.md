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

## EBS Exam Tips

- Volume of that instance and Instance are always in the same AZ.
- Let's say you have multiple EBS and want to change the volume type for some. You can do that just by clicking on Modify Volume.
- Root device volume will be deleted if you delete the instance (since by default delete on termination flag is on). However for additional volumes Delete on Termination flag is off. And those volumes will persist.
- Snapshots exists on S3. Think of snapshots as a photograph of that disk.
- Snapshots are point in time of copy of Volumes.
- Snapshots are incremental - This means that the only the blocks that have changed since your last snapshot are moved to S3.
- First snapshot takes some time.
- To create a snapshot of an EBS volume that serves as a root volume, you should stop the instance before taking the snapshot - it will consistence.
- However you can take a snap while the instance is running.
- You can create AMI's from both Volumes and Snapshots.
- You can changes EBS volumes size on the fly, including changing the size and storage type.
- *Migration1*: To move an EC2 volume from one AZ to another, take a snapshot of it, create an AMI from the snapshot and then use that AMI to launch an EC2 instance in another AZ.
- *Migration2*: To move an EC2 volume from one region to another, take snapshot of it, create an AMI from the snapshot and then copy that AMI to another region, and use that copied AMI to launch an instance in another Region.

## EBS vs Instance Store

You can select your AMI based on:

- Region
- Operating System
- Architecture
- Launch Permissions
- Storage for the root device (Root device volume)
	1. Instance store (Ephermal Storage)
	2. EBS backed

- *For EBS Volumes*: The root device for an instance launched from AMI is an Amazon EBS volume created from an Amazon EBS Snapshot
- *For Instance Store Volumes*: The root device for an instance launched from the AMI is an instance store volume created from a template stored in AMazon S3.

- Can't add Instance Store volume afte the instance has been launched, even if the the root device is instance store volume, still can't add those types later.

- You can't even stop an instance-store backed instance. You can reboot the instance or terminate. But you can't stop. Because if the instance is stopped and since it's only an ephermal storage -  All the data will be lost.

## Exams Tips 2

- Instance store volumes are sometimes called Ephemeral Storage.
- Instance store volumes cannot be stopped, If the underlying host fails, you will lose your data.
- EBS Backed instance can be stopped. You will not lose data if it is stopped.
- You can reboot both, you will not lose data.
- By default, both Root volumes will be deleted on termination. However with EBS volumes, you can tell AWS to keep the root device volume. You can't tell Instance-store backed volume to keep the Volume on termination - It WILL BE deleted.


# EBS Encryption
- Snapshots of encrypted volume are going to be encrypted.
- Volumes restored from encrypted snapshots are encrypted automatically.
- You can share snapshots, only if they are unencrypted.
- These snapshots can be shared with other AWS accounts or made public.

### Steps to encrypt the root-device volume.

- Create a snapshot of the unencrypted root device volume.
- Create a copy of the Snapshot and select the encrypt option.
- Create an AMI from the encrypted Snapshot.
- Use that AMI to launch a new encrypted instances.


# EC2 Placement Groups




# Misc

- Root Device volumes are not encrypted by default. When launching an instance the first team, the root device can't be encrypted at any cost.
- However you can later encrypt it using snapshots and copying image.
- Of the EBS volume, you can only create a SnapShot
- Programmatic Access is not that secure. When you run aws configure and enter your creds.
- Your Access Key and Secret Access Key ID are stored in aws ec2. It should never be stored there.
- Recommendation is to use IAM Roles.



