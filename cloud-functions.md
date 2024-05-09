
Timeout - 1 min to 60 mins(new version has longer timeout/higher memory supported)
2 versions

new version v2 -> build on top of cloud run and eventarc

Events from
- Cloud storage
- Cloud pub/sub
- http apis
- Firebase, Cloud firestore, Stack driver logging


Integrates with - Logs and monitoring(exec time, mem used) and are all available within same cloud functions dashboard

## Gen 2 (recommended)

### Features:
 - longer timeout - upto 60 mins
 - mem and cpu ( max 16GiB and 4 vCPU for one instance) (old one 6GB and 2vCPU)
 - Multiple versions and Traffic splitting (from underlying cloud run, can be managed from cloud run)
 - More events supported - cause of eventarc integration
 - Upto 1000 concurrent request can be handled by an instance (old one 1 conc request/instance )

Service account
- 1st gen - by default uses - App Engine Compute Default Service Account
- 2nd gen - by default uses - Default Compute Service Account

Creates cloud run - can view info on underlying cloud run in cloud run dashboard

Can set number of concurrent requests by one function instance (container)

```bash
gcloud functions deploy <func-name> 
--docker-registry
--docker-repository
--gen2 # (default 1st gen)
--runtime
--service-account 
--timeout
--max-instances
--min-instances

--source # zip file/Source repo url/local files
--trigger-topic / --trigger-bucket /  --trigger-http / --trigger-event-filters #(eventarc)
```


