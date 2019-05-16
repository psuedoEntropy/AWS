# DynamoDB

### What is DynamoDB?

- Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that millisecond latency at any scale.
- It is a fully managed database and supports both document and key-value data model.
- It's flexible data model and reliable performance make it a great fit for mobile, web, gaming, ad-tech, IoT, and many other applications.

### The basics of DynamoDB.

- Stored on SSD storage.
- Spread across 3 geographically distinct data centers.
- Eventual consistent reads (Default)
- Also have strongly consistent reads

## Evental Consistent Reads

- Consistency across all copies of data is usually reached within a second. Repeating a read after a short time would return the updated data. (Best read performance)

## Stronly Consistent Reads

- Needs to read that data within or less than one second.
- Returns a result that reflects all writes that received a successful response prior to the read.

