# VPC

#### What is a VPC?

- Think of a VPC as a virtual data center in the cloud.

- You have complete control of the IP address ranges you want to choose. The number of subnets of you want.
- Whether you'd like that subnet to be Internet facing or not. All this and more control is over to you.
- You can provision your web servers in public subnet and your DB Servers in Private subnets.
- There are multiple layers of security that you can implement (Route Table | NACLs | Security Groups)

- Additionally you can create a Hardware Virtual Private Network (VPN) between your corporate data center and your VPC and leverage the AWS cloud as an extension to your corporate data center.

### What can we do with VPC?

- Launch instances into a subnet of your choosing.
- Assign custom IP address ranges in each subnet.
- Configure route tables between subnets.
- Create Internet gateway and attach it to our VPC.
- Much better security control over your AWS resources.
- Subnet Network Access Control list

### Default VPC vs 	Custom VPC

- Default VPC is user friendly, allowing you to immediately deploy instances.
- All subnets in default VPC have a route out to the internet.
- Each EC2 instance has a both public and private IP addresses.

### VPC Peering

- Allows you to connect one VPC with another via a direct network route using private IP Addresses.
- Instances behave as if they were on the same private network. 
- You can peer VPCs with other AWS accounts as well as with other VPCs in the same account.
- Peering is a star configurarion, 1 central VPC connected to other 4 VPCs. There is NO Transitive Peering.

### 1 SUBNET == 1 Availability Zone
- Basically 1 subnet can not span multiple AZs. When you create a subnet you have to specify an AZ.