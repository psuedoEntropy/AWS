# Elasticache

- In Memory cache. Instead of relying on the slower disk-based databases, you use fast in-memory cache.
- Amazon.com - Top 10 purchased items. That is same, you don't query the DB.

# Memcached vs Reddis

### Memcache (Easy to get started with)

- Simple Cache to take some load of the database.
- Ability to scale horizontally.
- No Pub/Subscribing capabilities.
- No Persistance
- No Multi-AZ
- No Backup and restore capabilities.

### Reddis (Advanced)

- You need advanced data types.
- Ranking / Sorting data.
- Pub/Subscribing capabilities.
- Persistance
- Multi-AZ
- Backup and restore capabilities.

# Exam Tips

- Use Elasticache to increase database and web application performance.
- Reddis is Multi-AZ
- You can do backup and restores of Reddis.
- If you need to scale horizontally, use Memcached.