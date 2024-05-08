
Can run apps serverless


**Only** 1 App per project 
- single region only, for MR - create more app in other regions(new projects) (1 app per project)
- cant change the region later

- can have many different services (microservices, frontend backend etc)
- each service can have multiple versions of app code running on instances
- versions - can rollback and split traffic across versions
App -> Service -> Versions

## Environments:
- Standard (app runs in sandboxes)
    - v1 and v2
    - v1 older versions (java, python, php, go) - restrictions on network and libraries for python and php
    - v2 (new versions) (java, python, php, go,  node and ruby too)

- Flexible (app runs in containers)
    - need to provision instances
    - can support any runtime(java, python etc)
    - new local disk on startup - data gets lost each time
    - **minimum one instance should be running**


| x | Standard | Flexible |
| ---- | ---- | --- |
| Pricing | instance hours | infra provisioned - instances, disk etc|
| Scaling | Manual, Basic, Automatic | Manual, Automatic(no basic) - cant scale down to 0|
| Request timeout max| 1-10 mins| 60 mins|
| ssh | no | yes|

## Scaling
1. Manual - configure how many instances to run - increase/decrease manually
2. Basic - scale adhoc - when requests arrives
    - not suitable for _Flexible_ type
    - no instance will run when no requests arrives
    - can set max instances and idle timeout
    - use case: low cost, okay with high latency
3. Automatic - auto scale based on load
    - min and max instances (Like asg)
    - scale based on cpu utilization, no of requests, throughput utilizations
    - use case: continously tunning workloads

Using a combination of resident(always running) and dynamic(started on demand) instances
 - solves the problem of cold start (low latency)
 - also less cost (coz of dynamic instances)

[app.yaml](https://cloud.google.com/appengine/docs/standard/reference/app-yaml?tab=go#top) -> config for app engine about the app like `runtime: python39`

Can create versions and not promote it (using --no-promote), then use (--splits option to split traffic)
Can split traffic between versions active
Can access all versions with its specific url (though its not serving traffic in the main url)

- Auto scaling is handled in app.yaml

auto generated URLs:
- <proj-id>.<region-id>.r.appspot.com (default service)
- <service-name>-dot-<proj-id>.<region-id>.r.appspot.com (specific service)
- <version>-dot-<service-name>-dot-<proj-id>.<region-id>.r.appspot.com (specific version of a specific service)


[dispatch.yaml](https://cloud.google.com/appengine/docs/standard/reference/dispatch-yaml?tab=python) -> `gcloud app deploy dispatch.yaml`
- which route which service
- Can use load balancer with routing instead (alternative)


Splitting traffic 
- based on users' ip
    - could change when user switches network
    - if vpn is used by set of people - all their requests go to same version
- based on cookie - GOOGAPPUID
    - accurate, can be controlled from the application\
- randomly split traffic


`--image-url` option in cli - to give docker image url for Flexible environment

gcloud app versions start/stop <version> --service <service-name>

Can also:
- cron jobs, using cron.yaml (with interval and tasks) -> gcloud app deploy cron.yaml
- pick task form queue - add in queue.yaml with rate, retry options


Usecases:
- simple microservices

