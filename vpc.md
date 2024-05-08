Global resource - with subnets on multiple regions

Subnets - regional - spanned across AZs - HA and fault tolerance

every project has default VPC

1. Auto mode
    - subnets are automatically created in all regions
    - default vpc uses this mode
2. Custom mode (recommended for Prod)
    - subnets are not created automatically
    - have full control over cidr ranges

Private Google Access 
- enables instances in the subnet to access the google apis using private ips
- using private ips for communication - means the requests stays inside the private network

Flow logs can be enabled and used for troubleshooting

Class-less Inter Domain Routing


## Firewall rules
- priority - 0 (highest) to 65535 (lowest)
- default rules - with lowest priority - allow all egress, deny all ingress
- default rules - with second lowest priority(65534)
    - allow incoming traffic from instances in same network
    - allow ssh(22) and 3389(rdp for windows)
    - allow icmp - n/w layer - troubleshooting and monitoring

Ingress
- Source - (from where) could be CIDR range or a tag or service account
- Target - ( to which instances) use tag or service account or for all instances

Egress
- Target (from which instances) - instances filter (tag/service account/all)
- Destination - (to where)CIDR block

Each rule also has - protocol, port, action(allow/deny), priority, enforcement rule(enabled/disabled)


