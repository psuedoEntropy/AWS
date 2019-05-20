# Load Balancer

- When you're provisioning a Load Balancer, it gives you two option: 
	1. Internt Facing 
	2. Internal

- If you choose Internet facing, and you have two subnets, one Public and one Private witn no Internet access.
- Load Balancer will give you an error, that you can't have a Load Balancer on a subnet which has no Internet access
- If you only choose you Public facing subnet, Load balancer will again you an error that you need at least two subnets to provision a Load Balancer.


