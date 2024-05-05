Instance groups

1. Managed (MIG) - like ASGs in AWS
2. UnManaged 
    - just a group of instances - of different types
    - no autoscaling/auto healing etc

MIG
- Can add load balancer
- create zonal or regional(HA) MIGs
- Release
    - Rolling updates - update one by one to minimize downtime
        - (optional)Canary deployment - roll to few to test and then proceed to others
        - can choose Immediate update or update during resizing/cretaing new instances
        - can provide max surge(max create instance before removing old ones) and max unavailability
    - Restart/Replace (no updates) just restart all the VMs
        - can configure max surge and max unavailability too.
- Data persistance
    1. Stateful - For DBs - (preserves name, attached disk)
    2. Stateless - for others
- Autoscaling
    1. can be off
    2. only scale out
    3 scale out/scale in (both)
- cool down period
    - waiting seconds - till the app is ready to serve
- scale in contols
    - when removing instances add a limit based on time period
    - to prevent increased scaling down
    - dont scale more than %/number of instances in a specific time period
- Health check - auto healing

For
- HA even during updates
    - instance template with availability policy
        - automatic restart enabled
        - on host maintainance enabled
- Preventing frequent scale in scale out
    - initial delay option in health check
    - cool down period
