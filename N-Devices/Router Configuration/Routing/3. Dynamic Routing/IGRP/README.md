### IGRP (Interior Gateway Routing Protocol)

A **Cisco proprietary distance-vector** protocol.

**Key Points**

* Classful
* Composite metric (bandwidth, delay, load, reliability)
* Max hops: 255 (default 100)

**Advantages**

* Better than RIP
* Supports larger networks

**Disadvantages**

* Cisco-only
* Obsolete
* No VLSM/CIDR

### Command
```py
Router> enable
Router# configure terminal
Router(config)# router igrp 100
Router(config-router)# network 192.168.1.0
Router(config-router)# network 10.0.0.0
Router(config-router)# exit
Router(config)# exit

# Note: 100 is the Autonomous System (AS) number and must match on all routers.


```
---