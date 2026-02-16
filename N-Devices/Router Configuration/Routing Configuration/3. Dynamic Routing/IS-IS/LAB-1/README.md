## 📘 IS-IS (Intermediate System to Intermediate System) – 4 Router Lab

This README explains **IS-IS configuration for a 4-router topology** (R1, R2, R3, R4) with **fully commented commands**.

You can **copy–paste directly into Cisco Packet Tracer / GNS3**.

---

## 🧠 What is IS-IS?
> IS-IS is a **link-state routing protocol** mainly used by **ISPs**. It runs at **Layer 2** and is highly scalable and stable.

---

#### 🌐 Topology Overview

* 4 Routers: **R1, R2, R3, R4**
* Single IS-IS Area: `49.0001`
* All routers are **Level-1-2**
* IS-IS enabled **interface-wise**

---

#### 🔑 NET Address Structure (Important)

```py
49.0001.0000.0000.000X.00


| Field          | Meaning                       |
| -------------- | ----------------------------- |
| 49             | Private AFI                   |
| 0001           | Area ID                       |
| 0000.0000.000X | System ID (Unique per router) |
| 00             | NSEL (Always 00)              |

```
---

### IS-IS Configuration
> 🟦 R1 – IS-IS Configuration

```py
R1> enable                     # Enter privileged mode
R1# configure terminal         # Enter global configuration

R1(config)# router isis        # Start IS-IS routing process

R1(config-router)# net 49.0001.0000.0000.0001.00   # Set unique NET for R1
R1(config-router)# is-type level-1-2               # Enable L1 & L2 routing
R1(config-router)# exit

# Enable IS-IS on connected interfaces
R1(config)# interface gigabitEthernet0/0
R1(config-if)# ip router isis
R1(config-if)# exit

R1(config)# interface gigabitEthernet0/1
R1(config-if)# ip router isis
R1(config-if)# exit

R1(config)# interface gigabitEthernet0/2
R1(config-if)# ip router isis
R1(config-if)# exit
```

---

> 🟦 R2 – IS-IS Configuration
```py
R2> enable
R2# configure terminal

R2(config)# router isis
R2(config-router)# net 49.0001.0000.0000.0002.00   # Unique NET for R2
R2(config-router)# is-type level-1-2
R2(config-router)# exit

R2(config)# interface gigabitEthernet0/0
R2(config-if)# ip router isis
R2(config-if)# exit

R2(config)# interface gigabitEthernet0/1
R2(config-if)# ip router isis
R2(config-if)# exit

R2(config)# interface gigabitEthernet0/2
R2(config-if)# ip router isis
R2(config-if)# exit
```

---

> 🟦 R3 – IS-IS Configuration

```py
R3> enable
R3# configure terminal

R3(config)# router isis
R3(config-router)# net 49.0001.0000.0000.0003.00   # Unique NET for R3
R3(config-router)# is-type level-1-2
R3(config-router)# exit

R3(config)# interface gigabitEthernet0/0
R3(config-if)# ip router isis
R3(config-if)# exit

R3(config)# interface gigabitEthernet0/1
R3(config-if)# ip router isis
R3(config-if)# exit

R3(config)# interface gigabitEthernet0/2
R3(config-if)# ip router isis
R3(config-if)# exit
```

---

> 🟦 R4 – IS-IS Configuration

```py
R4> enable
R4# configure terminal

R4(config)# router isis
R4(config-router)# net 49.0001.0000.0000.0004.00   # Unique NET for R4
R4(config-router)# is-type level-1-2
R4(config-router)# exit

R4(config)# interface gigabitEthernet0/0
R4(config-if)# ip router isis
R4(config-if)# exit

R4(config)# interface gigabitEthernet0/1
R4(config-if)# ip router isis
R4(config-if)# exit

R4(config)# interface gigabitEthernet0/2
R4(config-if)# ip router isis
R4(config-if)# exit
```

---

#### 🔍 Verification Commands

```py
show isis neighbors      # Check IS-IS adjacencies
show isis database       # View link-state database
show ip route isis       # View routes learned via IS-IS
```

---

#### ✅ Expected Result

* All routers form **IS-IS neighbors**
* Full routing table visibility
* Routes marked with **`i`**

---

## NOTE:
```py
Use one of these routers:

Router Model	        IS-IS Support
❌ Router-PT-Empty	   NO
❌ 1841	               NO
❌ 2811                 NO
✅ 2911 (with advanced image)	YES (sometimes)
✅ CSR1000v (GNS3)	    YES
✅ 7200 (GNS3)	       YES
```