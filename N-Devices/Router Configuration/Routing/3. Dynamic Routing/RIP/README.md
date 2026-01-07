### RIP v1 Routing Information Protocol

> • Open Standard Protocol\
> • Classful routing protocol\
> • Updates are broadcasted via 255.255.255.255\
> • Administrative distance is 120 \
> • Metric Hop count\
    `Max Hop counts: 15` | ` Max routers: 16`\
> • Load Balancing of 4 equal paths\
> • Used for small organizations\
> • Exchange entire routing table for every 30 seconds


### Rip Timers
---
> Update timer : `30 sec`
>   + Time between consecutive updates

> Invalid timer : `180 sec`
>   + Time a router waits to hear updates
>   + The route is marked unreachable if there is no update during this interval.\

> Flush timer : `240 sec`
>   + Time before the invalid route is purged from the routing table


---
<img src="img/1.png">

---

### Configuring RIP v1
```py
Router(config)# router rip
Router(config-router)# network <Network ID>
```
#### [R1] On Hyderabad Router
```py
HYDERABAD # config t
HYDERABAD(config) # router rip
HYDERABAD(config-router) # network 10.0.0.0
HYDERABAD(config-router) # network 1.0.0.0
HYDERABAD(config-router) # exit
HYDERABAD(config) # exit
```

##### [R2] On KSA Router
```py
KSA # config t
KSA(config) # router rip
KSA(config-router) # network 20.0.0.0
KSA(config-router) # network 1.0.0.0
KSA(config-router) # exit
KSA(config) # exit
```