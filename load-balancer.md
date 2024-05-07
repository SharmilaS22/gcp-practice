## Load Balancer

- Global LB with single anycast IP
- supports internal Load balancing


App Layer - http/https/smtp/ftp
N/W Layer - tcp/udp (high performance)
    - gaming, live streaming

### LB Types
1. TCP
2. HTTP
3. UDP(only single region)

### backend configuration - Like target group
    - can also host static content with CDN
    - can divide the requests
        - based on path/host(sub-domain)/http headers/methods

### SSL/TLS Offloading(Termination)
Client to LB -> https (secure)
LB to Backend(TG) -L> through google network (can disable ssl/tls)

### Choosing load balancer
- https - regional/global
- tcp 
    - ssl offload -> ssl proxy
    - otherwise 
        - global/ipv6 -> tcp proxy
        - otherwise
            - want to preserve client ips(no proxy) -> n/w lb
            - else -> tcp proxy
- udp - n/w lb

## Features of load balancer
| LB                | Type                          |
|------------------------|--------------------------------------|
| ssl proxy   | tcp with ssl offload  |
| tcp proxy   | tcp w/o ssl offload   |
| n/w lb      | tcp/udp with no proxy |



