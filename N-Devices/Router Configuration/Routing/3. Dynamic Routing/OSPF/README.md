### OSPF (Open Shortest Path First) 
> •  OSPF stand for Open Shortest path first\
> •  Standard protocol\
> •  It’s a link state protocol\
> •  It uses SPF (shortest path first) or dijkistra algorithm\
> •  Unlimited hop count\
> •  Metric is cost (cost=10 ^8/B.W.)\
> •  Administrative distance is 110\
> •  It is a classless routing protocol\
> •  It supports VLSM and CIDR\
> •  It supports only equal cost load balancing\
> •  Introduces the concept of Area’s to ease management and control traffic

> •  Provides hierarchical network design with multiple different areas\
> •  Must have one area called as area 0\
> •  All the areas must connect to area 0\
> •  Scales better than Distance Vector Routing protocols.\
> •  Supports Authentication\
> •  Updates are sent through multicast address 224.0.0.5\
> •  Faster convergence.\
> •  Sends Hello packet every 10 seconds\
> •  Trigger/Incremental updates\
> •  Router’s send only changes in updates and not the entire routing tables in periodic updates


A **link-state** protocol using **Dijkstra’s algorithm**.

**Key Points**

* Classless
* Metric: Cost
* Area-based (Area 0 = backbone)
* Fast convergence
* Multicast: 224.0.0.5, 224.0.0.6

**Advantages**

* Highly scalable
* Fast convergence
* Efficient bandwidth use

**Disadvantages**

* Complex configuration
* High CPU/RAM usage

### Commands (Single-Area OSPF – Cisco IOS)
```py
Router> enable
Router# configure terminal
Router(config)# router ospf 1
Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
Router(config-router)# network 10.0.0.0 0.255.255.255 area 0
Router(config-router)# exit
Router(config)# exit

### 1 is the Process ID (locally significant).
Router(config)# router ospf 1
Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
Router(config-router)# network 172.16.0.0 0.0.255.255 area 1

### Verification Commands
show ip ospf
show ip ospf neighbor
show ip route ospf
```
---