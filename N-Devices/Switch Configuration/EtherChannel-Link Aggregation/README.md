
[1️⃣ What is EtherChannel (Link Aggregation)?](#1️⃣-what-is-etherchannel-link-aggregation)\
[2️⃣ LACP (Link Aggregation Control Protocol)](#2️⃣-lacp-link-aggregation-control-protocol)\
[3️⃣ PAgP (Port Aggregation Protocol)](#3️⃣-pagp-port-aggregation-protocol)\
[4️⃣ Static EtherChannel (Mode ON)](#4️⃣-static-etherchannel-mode-on)\
[5️⃣ EtherChannel Requirements](#5️⃣-etherchannel-requirements)\
[6️⃣ Load-Balancing Methods](#6️⃣-load-balancing-methods)\
[7️⃣ show etherchannel summary Output Example](#7️⃣-show-etherchannel-summary-output-example)


### 1️⃣ What is EtherChannel (Link Aggregation)?
> EtherChannel bundles multiple physical Ethernet links into one logical link to increase bandwidth and provide redundancy.

> Key Features
   + Combines 2–8 physical ports
   + Appears as one logical interface (Port-channel)
   + STP treats it as one link

> ✅ Benefits
  + Higher bandwidth
  + Redundancy (fault tolerance)
  + Load balancing
  + Simplified STP topology
---

### 2️⃣ LACP (Link Aggregation Control Protocol)
+ 📘 Overview
  + IEEE Standard: 802.3ad (now 802.1AX)
  + Open standard (multi-vendor support)
  + Automatically negotiates the channel

> 🔹 LACP Modes
```py
| Mode    | Description                     |
| ------- | ------------------------------- |
| active  | Actively sends LACP packets     |
| passive | Waits for LACP packets          |
| on      | Forces channel (no negotiation) |

```

#### 🖥 Example: LACP Between 2 Switches
> SW1 ↔ SW2
> nterfaces: Fa0/1, Fa0/2

> 🔧 SW1 Configuration
```py
Switch(config)# interface range fa0/1 - 2
Switch(config-if-range)# channel-group 1 mode active
Switch(config-if-range)# exit

Switch(config)# interface port-channel 1
Switch(config-if)# switchport mode trunk
```
> 🔧 SW2 Configuration
```py
Switch(config)# interface range fa0/1 - 2
Switch(config-if-range)# channel-group 1 mode active
Switch(config-if-range)# exit

Switch(config)# interface port-channel 1
Switch(config-if)# switchport mode trunk
```
> 🔎 Verification Commands
```py
show etherchannel summary
show etherchannel port-channel
show lacp neighbor
```


---
### 3️⃣ PAgP (Port Aggregation Protocol)
> 📘 Overview
  + Cisco proprietary protocol
  + Works only on Cisco devices

🔹 PAgP Modes
```py
| Mode      | Description                     |
| --------- | ------------------------------- |
| desirable | Actively negotiates             |
| auto      | Passively waits                 |
| on        | Forces channel (no negotiation) |

```
👉 One side must be `desirable`

> 🖥 Example: PAgP Between 2 Switches
> 🔧 SW1
```py
Switch(config)# interface range fa0/1 - 2
Switch(config-if-range)# channel-group 2 mode desirable
Switch(config-if-range)# exit

Switch(config)# interface port-channel 2
Switch(config-if)# switchport mode trunk
```
> 🔧 SW2
```py
Switch(config)# interface range fa0/1 - 2
Switch(config-if-range)# channel-group 2 mode auto
Switch(config-if-range)# exit

Switch(config)# interface port-channel 2
Switch(config-if)# switchport mode trunk
```
> 🔎 Verification
```py
show etherchannel summary
show pagp neighbor
```
---

### 4️⃣ Static EtherChannel (Mode ON)
> 📘 Overview
   + No negotiation protocol
   + Both sides must be configured manually
   + Risky if mismatch occurs

> 🖥 Example: Static EtherChannel
> 🔧 SW1
```py
Switch(config)# interface range fa0/1 - 2
Switch(config-if-range)# channel-group 3 mode on
Switch(config-if-range)# exit

Switch(config)# interface port-channel 3
Switch(config-if)# switchport mode trunk
```
> 🔧 SW2
```py
Switch(config)# interface range fa0/1 - 2
Switch(config-if-range)# channel-group 3 mode on
Switch(config-if-range)# exit

Switch(config)# interface port-channel 3
Switch(config-if)# switchport mode trunk
```

---
### 5️⃣ EtherChannel Requirements

+ ✔ Same speed
+ ✔ Same duplex
+ ✔ Same VLAN
+ ✔ Same trunk/access mode
+ ✔ Same allowed VLANs (if trunk)
+ ✔ Same native VLAN

---

### 6️⃣ Load-Balancing Methods
📘 What is Load Balancing?
> Switch distributes traffic across bundled links using a hashing algorithm.

🔹 Common Methods
```py
| Method       | Description              |
| ------------ | ------------------------ |
| src-mac      | Based on source MAC      |
| dst-mac      | Based on destination MAC |
| src-dst-mac  | Both MAC addresses       |
| src-ip       | Source IP                |
| dst-ip       | Destination IP           |
| src-dst-ip   | Both IPs (Most common)   |
| src-port     | TCP/UDP source port      |
| src-dst-port | Layer 4 ports            |

```
> 🔧 Configure Load Balancing
```py
# Check current method:
show etherchannel load-balance

# Change method:
Switch(config)# port-channel load-balance src-dst-ip
```
---
### 7️⃣ show etherchannel summary Output Example
```py
Group  Port-channel  Protocol    Ports
------+-------------+----------+-------------------------
1      Po1(SU)        LACP      Fa0/1(P) Fa0/2(P)

# 🔎 Legend

S = Layer 2
U = In use
P = Bundled in port-channel
```
---
#### 🔥 LACP vs PAgP vs Static Comparison
```py
| Feature        | LACP         | PAgP       | Static |
| -------------- | ------------ | ---------- | ------ |
| Standard       | IEEE         | Cisco      | None   |
| Vendor support | Multi-vendor | Cisco only | Multi  |
| Negotiation    | Yes          | Yes        | No     |
| Safer          | ✅            | ✅          | ❌      |

```