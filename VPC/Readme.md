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
- /28 is the least CIDR range provided by AWS

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

------------------------------------------- Practical | Lab | Experiment --------------------------------

- When we create a New VPC
	1. No Subnets are created.
	2. No Internet Gateway is created.
	4. A default Route table is created. (allows subnet to talk to each other)
	4. A default Network ACL is created. (User-Friendly)
	5. A default Security Group is created. (User-Friendly)

---------------------------------------------------------
- One account's US-East-2a might be different from other account's US-East-2a
- Amazon reserves 5 IP address 
- Basically the First 4 and the Last IP address in your CIDR range is not accessible to you

- 10.0.0.0: Network Address
- 10.0.0.1: Reserved by AWS for VPC Router
- 10.0.0.2: Reserved by AWS as base address
- 10.0.0.3: Reserved by AWS for future use
- 10.0.0.255: Network broacast address

- One Internet Gateway per ONE VPC


-----------------------------------------------------------

- NAT Instance is just a single EC2 Instance that you provision from community AMIs
- NAT Gateways are highly available gateways with a Elastic IP Address (chargeable)
- Both get provisioned in the Public Subnet.
- You make an entry in the route table of the Private Subnet, where a route is [Destination is 0.0.0.0/0] and source is [NAT Instance ENI or NAT gateway ID]
- Source and Destintion check should be disabled on the NAT Instance.
- NAT instance is acting like a bridge b/w Private Subnet and Internet. SO it's not a source neither a destination.



