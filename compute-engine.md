
## Google Compute Engine

Load balancing, Auto scaling, Attaching storage, network interfaces, boot disk(AMI/OS)

## Terms:
- External IP (Public)
- Internal IP (Private)
- External IP Address  
    - EIP (static ip addresses) - reserve static address 
    - same region as the VM
    - can assign to a VM (even when VM stops the IP continue to be attached)
    - billed even when not used
- Startup script - (User script)
- Instance template (launch template)
    Can't modify the template after creating


### Live migration

- during maintainance
- migrate the vm instance to another host(same zone) - not supported for GPUs

## Availability Policy
- On host maintainance - migarting the VM (is default option)
- can also set to stop the instance if okay with downtime
- Automatic Restart - restart when terminated due to non-user-initiated reasons

