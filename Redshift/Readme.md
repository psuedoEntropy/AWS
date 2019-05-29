# Redshift

- Redhift is a fast and powerful solution by AWS for data warehousing.
- Petabyte scaling.
- Start small with no commitments and move up to $1000/TeraByte per year. (cheap)
- Used for OLAP transactions (Online Analytics Processing)

### Data Warehousing databases use different type of architecture from a database perspective and infrastructure layer.

## Redshift can configured as follows

- Single Node (160 Gb)
- Multi-Node
	1. Leader Node (manages client connection and received queries)
	2. Compute Node (store data and perform queries and computations). Up to 128 compute nodes.

- Amazon Redshifts uses amazing and muliple compression techniques.
- Column-wise data is pretty much the same, so you can compress more with redshift.
- Redshift doesn't require indexed or materialized views.
- When loading data into an empty table, Amazon Redshift automatically samples your data and selects the most appropriate scheme.

### Massively Parellel Processing

- Amazon redshifts automatically distibutes data and query load across all nodes.
- You can easily scale out with Amazon Redhift by adding nodes to your schema which will take the extra load.

## Backups

- Enabled by default with 1 day retention period.
- Maximum retention period is 35 days.
- Redshift always attempts to maintain at least 3 copies of your data (original + replica on compute nodes + backup in S3)
- Redshift can asynchronously replicate your snapshots to S3 in another region for disaster recovery.

- Only charged for Backups and compute nodes (not the leader node) and data transfer.

## Security Consideration

- Encrypted in transit using SSL.
- Encrypted at rest using AES-256 encryption.
- By default Redshift takes care of key-management. But you can manage your own keys if you wish to using HSM or KMS.

## Redshift Availability

- Can't turn AZ on yet.
- Can restore snapshots to a new AZs in the event of an outage.

 
 # Exam Tips

 - Redshift is used for business intelligence.
 - Only available in 1 AZ
 - Backsups are enabled by default with 1 day retention
 - Can have up to 35 day retention day period
 - Redshift always try to maintain at least 3 copies of your data (original + replica + compute nodes and a backup in Amazon S3)
 - Redshift can asynchronously replicate your snapshots to S3 in another region for disaster recovery.