#### IS-IS (Intermediate System to Intermediate System)

A **link-state** protocol widely used by **ISPs**.

**Key Points**

* Level-1 and Level-2 areas
* Classless
* Runs at Layer 2
* Very scalable

**Advantages**

* Extremely stable
* Fast convergence
* Suitable for large networks

**Disadvantages**

* Complex
* Less common in enterprises

### Command
```py
Router> enable
Router# configure terminal
Router(config)# router isis
Router(config-router)# net 49.0001.1921.6800.1001.00
Router(config-router)# is-type level-1-2
Router(config-router)# exit


Router(config)# interface gigabitEthernet0/0
Router(config-if)# ip router isis
Router(config-if)# exit

### The net command defines the Network Entity Title (NET) for IS-IS.

### Verification Commands 
show isis neighbors
show isis database
show ip route isis
```
---