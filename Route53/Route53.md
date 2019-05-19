# Route 53

- 53 is the port number of DNS
- DNS is used to convert human-friendly domain names (phirani.co.in) into an IP address (12.3.22.234)
- IP address come in two different forms IPv4 and IPv6.

### Top level domains

.*com* | |
.*edu* | |
.*gov* | |

## Second Level Domain

.*co*.in | |
.*gov*.uk | |

## SOA

- Every DNS record starts with a SOA (Start if authority record)

- The name of the server that supplied the data for the zone.
- The adminstrator of the zone.
- The current version of the data file.
- The default number of seconds for the time-to-live file on resouce records.

## Example

- you fire up sanyamphirani.com
- Broweser doesn't the IP address of that domain
- Browser will go to the top level domain server --> ns.awsdns.com
- Top level will have the Name Server record, which will query that NS record.
- NS record will give us SOA record. In that SOA we will have have IP address mapping.

# A Record

- An "A" record is the fundamental type of DNS record. The "A" in A record stands for Address. The A record is used by a computer to translate the name of the domain to an IP address. For example http://sanyam.com might point to http://123.0.0.23:80

# TTL

- The lenght of time in seconds for which the DNS record is cached - either on the local computer or the resolving server
- The lower the time to live, the faster changes to DNS records take to propogate throughout the internet.

# C-Name

- A canonical name can be used to resolve one domain to another. For example, you may have a website m.facebook.com but you also want mobile.facbook.com to resolve to m.facebook.com as well. Instead of mapping different IP to these different DNS. you have one IP to which both these domain resolve to.

# Alias-Record

- Alias record are used to map resource record set in your hosted zone to Elastic Load Balancers, Cloud Front distributions, or S3 buckets that are configured as websites.
- Alias record work like C-Name in that you can map one DNS name (sanyam.com) to another target DNS name (elb.amazonaws.com)

# C-Name vs Alias Record

- A C-Name can't be used for naked domain name. You can't have a CName for http://acloud.guru, it must be either an A record or an Alias record.

- You can buy domain names directly from AWS and it can take up to 3 days for regestering it.

## Routing policies available on Route53

- Simple Routing
- Latency Based Routing
- Failover-based routing
- Geolocation Routing
- Geop Proximity Routing (Traffic flow only)
- Multi-Value Answer routing

# Simple Routing policy

- Where you only have one record with multiple IP Address. If you specify multiple values in a record, Route 53 returns all values to the user in a random order.


# Weighted Routing Policy

- Allows you to split your traffic based on different weights assigned.
- 10% to US-EAST-1 and 90% to EU-EAST-2
- In weighted routing policy you create multiple record set.
|Weight 3 to One IP | Weight 2 to Second IP | Weight 5 to Third IP
|3/3+2+5		   | 2/3+2+5			   | 5/3+2+5
|	3/10		   |	2/10			   | 5/10
|	30%			   | 	20%				   | 	50%