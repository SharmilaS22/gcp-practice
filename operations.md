### Cloud monitoring
- measure metrics
- create graphs and dashboards
- configure alerts

Group monitoring info many projects (in one or many accounts) using
Workspace

create workspace in a project and add other projects to the workspace


Instance metrics:
- CPU use
- disk traffic
- n/w traffic
- uptime check and alert

- Can use _Cloud Monitoring Agent_ in the instance to get more info.

### Cloud Logging

- real time
- log management and analysis
- can store, search, analyze and alert on data

- fully managed
- ingest log from any source
- auto logging for google managed services
- for Instances - _Logging Agent_(fluentd) need to be installed
- for VMs on prem - use BindPlane tool from Blue Medora or use gcp cloud logging api

Features: 
- Logs Explorer - use queries
- Logs dashboard - visualisation
- Logs metrics - capture metrics from logs
- Logs router - route logs from various sources to different destinations.


Axis transparency logs

Audit logs

1. admin activity logs
2. data access logs
3. system event logs
4. policy denied logs


Log Router:
- two types - logging bucket
    - _Required - locked (admins activity, sys events, access transparency log) - no charge
        - rertained for 400 days (cant change or delete anything)
    - _Default - (all other logs)
        - the sinks can be disabled
        - billed/charges applicable
        - retained 30 days(1 day to 10 years)
- can export to DBs, storage
    - long term retention (compliance needs)
    - can export to GCS (bucket), Big query (dataset) -> sql query, cloud pubsub (topic) -> to others
    - create _sinks_ to these export destinations - also has filter(include/exclude)
    - to retain logs - min cost - export to GCS bucket 
    - Google Data Studio for viz

### Cloud Trace
- distributed tracing service
- **latency data** from compute engine, GKS, app engine etc
- trend of latency, avg latency
- trace client lib for C#, Go, Java, Node.js, PHP, Python and Ruby


## Cloud Profiler

- identify performance bottlenecks(in prod) - by gathering metrrics from systems
- two components - Profiling agent, Profiler Interface(viz)

### Error Reporting
- identify prod problems in real time

- collect all errors - centralized error management

- **Firebase Crash reporting** for errors in android and iOS applications
- Go, Java, .net, Node.js, PHP, Python, and Ruby
reported using cloud logging or by calling Error Reporting API
Can be accessed from desktop, cloud console mobile app

### 
