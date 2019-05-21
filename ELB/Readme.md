# Load Balancer

### 3 Different Types of Load Balancers

- Application Load Balancers
	1. They are best suited for load balancing of HTTP and HTTPS traffic. They operate at Layer 7 and are application aware. They are intelligent, and you can create advanced requests routing, sending specified requests to specific web servers.
	2. See, they you have changed your local language to french? Route your requests to french servers and load balance there.

- Network Load Balancers
	1. They are best suited for load balancing of TCP traffic where extreme performance is required. Operating at the connection level (Layer 4). Network load balancers are capable of handling millions of requests per second, while maintaining ultra-low latencies.
	2. Usecase: Extreme Perforamance
- Classic Load Balancers
	1. They are the legacy Elastic Load Balancers. You can load balance HTTP/HTTPS Applications and use layer-7 specific features such as X-Forwarded and sticky sessions. You can also use strict Layer 4 load balancing for applications that rely purely on thr TCP protocol.

- If you application stops responding, the ELB (Classic) responds with 504 error.
- This means that the application is having issues. This could be either at the web-server layer or at the Database Layer. Identify where the application is failing and scale it up or out where possible.

- X-Forwarded-For header the IP address of the User. EC2 instance will get ELB's address as the User address. But in that ELB config, there will be a X-Forwarded-For header which will be the IP Address of the User

### Cross-Zone Load Balaning
- Cross-zone load balancing distributes traffic evenly across all targets in the Availability Zones enabled for the load balancer.




- When you're provisioning a Load Balancer, it gives you two option: 
	1. Internt Facing 
	2. Internal

- If you choose Internet facing, and you have two subnets, one Public and one Private witn no Internet access.
- Load Balancer will give you an error, that you can't have a Load Balancer on a subnet which has no Internet access
- If you only choose you Public facing subnet, Load balancer will again you an error that you need at least two subnets to provision a Load Balancer.


