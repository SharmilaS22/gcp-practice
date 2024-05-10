- Availability - 4 9's 99.99% is good
- Durability   - 11 9's 99.999999999% is good

Strong consistency - sync replication to all (for usecases needing it)

Read-after-write consistency - write is fast, updates are slow
---
## Cloud SQL

It supports MySQL, PostgreSQL and SQL server. 
Regional service 
HA 99.95% 
SSD and HDD 
up to 416 GB of RAM 30 TB of data storage 

Cloud Spanner 
- to deal with huge volumes of data
- to go global
- higher availability. 99.999%
- Infinite scaling

---

### Cloud SQL features: 
- automatic encryption, maintainance and updates
- Auto scaling of storage w/o downtime
- Point in time recovery (provide how many days?) - binary logging Need to be enabled
- Auto backups
- zonal
- HA -> standby for Automatic failover
- Read replica - cross zone/region, can also use external(other service than CloudSQL)
- auto backup and binary logging need to be enabled for HA and read replica
- private ip /public ip
- preferred window for maintainance
- Migration from others sources using DMS
- Export data in SQL and CSV format


HA - auto failover 
- sync replication
- no auto revert back to primary zone 

---

### Cloud Spanner
- Globally distributed database
- High availability 99.999%
- Cloud playground to interact with DB, table etc
- Strong transactional consistency
- Scales to PBs of Data
- Scares horizontally for both reads and rights - CloudSQL provides read replica, but you can't scale write operations
- Have both regional(3 RW replicas in 3 zones) and multi regional configurations
- Expensive, compared to CloudSQL
- Can export data


-----
### Cloud Datastore - NoSQL
- Highly scalable
- for Few TBs of data (for bigger volumes, BigTable is recommended)
- Supports transaction with SQL like queries, does not support joins or sum operation
- Use cases with flexible schema
- Can export data from Gloud CLI?

### Firestore (next gen of DataStore)
- multi device access
- offline mode
- data sync across multiple devices
- provides client side libs - for all platforms
- Can use **datastore mode** to migrate from datastore / use **native mode** for fresh db

---

### Cloud BigTable (HBase - OSS)
- PBs of data 
- Not serverless, scale horizontally
- Wide columns (columns of columns - grouping of columns)
- only single row transaction is supported
- row is key(id) and value
- scale PBs of data with milli second responses - low latency
- usecases - Streams, graph data, real time analytics
- can use Cloud Dataflow to export data to CloudStorage(GCS(S3)) 
- cant export data directly, use Java apps/HBase commands to export
- CLI is `cbt` instead of `gcloud`

---

### MemoryStore
- in memory datastore
- fully managed(replica, failover, patching etc)
- redis(low latency, persistence, HA), memchached(only caching, like session etc)
- HA 99.9%