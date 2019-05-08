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

### Dedicated Hosts pricing is useful for:

- Useful for regulatory reuirements that may not support multi-tenant virtulization.
- Great for licensing which does not support multi-tenancy or cloud deplyoments.
- Can be purchased as a reservation for up to 70% off the on-demand price.

### Fight Dr McPxz AU
|F |I |G |H |T |D |R |M |C |P |X |Z |A |U |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
|FGPA|IOPS|Graphics|High Disk Throughput|Cheap General Purpose|Density|RAM|Main choice for GP|Compute|Graphics|Extreme Memory|Arm-based workloads|Bare metal|




# Misc

- Root Device volumes are not encrypted by default.
