## IAM

###### IAM allows you to manage users and their level of access to the AWS Console.

- Centrailsed control of your AWS account.

- Shared access to your AWS account.

- Granular Permission (pick out the services that you wanna give users to access to)

- Identity Federation (Active Directory,windowsPCPassword, Facebook, Linkedin)
	- End-Users on a Mobile DEV Game, need to access AWS storage, they can use FB account to access that info.

- Multifactor Authentication.

- Provides Temporary access to users/devices and services where necessary.
		- mobile end users storing data to your AWS account, only give access when they're using the app
		- we can also have SMS based MFA itegrated with the end-user login using Identity Federation

- Allows you to set up your own password rotation policy.

- Integrates with many different AWS services.

- Compliance with PCI DSS.



###### Users
	- End users such as people, employees of the organization.


###### Groups
	- A collection of users. Each user in the group will inherit the permission of the group.


###### Policies  == Permissions
	- Policies are made up of documents called Policy documents. These documents are in a format called JSON, and
	theey give permissions to as to what a Role/Group/User is able to do
	- By default, IAM users, groups, and roles have no permission.


###### Roles
	- You create roles and then assign them to AWS resources.
	- A role is a way to allow one part of AWS service to do something with another part of AWS service
	- S3-Admin role to EC2 Server (that EC2 server can now talk to S3 buckets)
	- IAM roles are not associated with a specific user or group. Instead, trusted entities assume roles, such as IAM users, applications, or AWS services such as EC2.
	- You are limited to 1,000 IAM roles under your AWS account.
	- You can assign a role to an EC2 instance that is already running. 
	- A role can have no more than 10 managed policies attached.

