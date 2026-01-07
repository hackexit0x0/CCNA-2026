### EIGRP (Enhanced Interior Gateway Routing Protocol)

What is EIGRP?
> EIGRP is a hybrid routing protocol (distance-vector + link-state features) that provides fast convergence, efficient bandwidth usage, and loop-free routing.

> •  Cisco proprietary protocol\
> •  Classless routing protocol\
> •  Includes all features of IGRP

> •  Metric (32 bit) : Composite Metric (BW + Delay + load + MTU + reliability )\
> •  Administrative distance is 90\
> •  Updates are through Multicast (224.0.0.10 )\
> •  Max Hop count is 255 (100 by default)\
> •  Supports IP, IPX and Apple Talk protocols\
> •  Hello packets are sent every 5 seconds\
> •  Convergence rate is fast 

> •  First released in 1994 with IOS version 9.21.\
> •  Support VLSM and CIDR\
> •  It uses DUAL (diffusion update algorithm)\
> •  Summarization can be done on every router\
> •  Supports equal and unequal cost load balancing

> •  It maintains three tables\
– Neighbor table\
– Topology table\
– Routing table

### Disadvantages of EIGRP
• Works only on Cisco Routers

> Configuring EIGRP
```py
Router(config)# router eigrp <as no>
Router(config-router)# network <Network ID>
```
---
<img src="img/1.png">

---

> [R1] ON HYD:
```py
HYD # config terminal
HYD(config) # ip routing
HYD(config) # router eigrp 10 ( Autonomous system NO is 10)
HYD(config-router) # network 1.0.0.0
HYD(config-router) # network 10.0.0.0
HYD(config-router) # exit
HYD(config) # exit

HYD # show ip route
```

> [R2] ON KSA:
```py
KSA # config terminal
KSA(config) # ip routing
KSA(config) # router eigrp 10 ( Autonomous system NO is 10)
KSA(config-router) # network 20.0.0.0
KSA(config-router) # network 1.0.0.0
KSA(config-router) # exit
KSA(config) # exit

KSA # show ip route
```