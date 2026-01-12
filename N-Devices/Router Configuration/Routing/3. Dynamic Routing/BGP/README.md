### BGP (Border Gateway Protocol)

A **path-vector** protocol used for **Internet routing**.

**Key Points**

* Exterior Gateway Protocol (EGP)
* Runs on TCP port 179
* Policy-based routing
* Extremely scalable

**Advantages**

* Internet-scale routing
* Highly reliable
* Supports complex policies

**Disadvantages**

* Very complex
* Slow convergence
* Resource intensive

### Command
```py
Router> enable
Router# configure terminal
Router(config)# router bgp 65001
Router(config-router)# neighbor 192.168.1.2 remote-as 65002
Router(config-router)# network 10.0.0.0 mask 255.0.0.0
Router(config-router)# exit
Router(config)# exit

### 65001 and 65002 are Autonomous System numbers.

#### Verification Commands
show ip bgp
show ip bgp summary
show ip route bgp
```
---
