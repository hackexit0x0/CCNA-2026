# 🔁 OSPF to BGP Routing Configuration (4-Router Topology)

This project demonstrates the **conversion of an OSPF-based routing topology into BGP** while keeping the **same physical and IP topology**.

The lab is ideal for:
- CCNA / CCNP practice
- Understanding **OSPF vs BGP**
- GNS3 / Packet Tracer routing labs
- Interview preparation

<img src="image.png">

---

## 🧩 Network Topology

### Router Positions
| Router | Position |
|------|---------|
| R1 | Top-Left |
| R2 | Top-Right |
| R3 | Bottom-Right |
| R4 | Bottom-Left |

---

## 🌐 Router-to-Router Links

| Link | Network |
|----|--------|
| R1 ↔ R2 | 10.0.0.0 /30 |
| R2 ↔ R3 | 20.0.0.0 /30 |
| R3 ↔ R4 | 30.0.0.0 /30 |
| R4 ↔ R1 | 40.0.0.0 /30 |

---

## 🖧 LAN Networks

| Router | LAN Network |
|------|------------|
| R1 | 192.168.1.0 /24 |
| R2 | 192.168.2.0 /24 |
| R3 | 192.168.3.0 /24 |
| R4 | 192.168.4.0 /24 |

---

## 🔢 BGP Autonomous System Numbers

| Router | AS Number |
|------|----------|
| R1 | 65001 |
| R2 | 65002 |
| R3 | 65003 |
| R4 | 65004 |

> 📌 **eBGP is used** (each router in a different AS)

---

## 🚀 BGP Configuration

>  🔹 R1 (AS 65001)
```py
router bgp 65001
 bgp router-id 1.1.1.1
 neighbor 10.0.0.2 remote-as 65002
 neighbor 40.0.0.1 remote-as 65004
 network 192.168.1.0 mask 255.255.255.0
```
> 🔹 R2 (AS 65002)
```py
router bgp 65002
 bgp router-id 2.2.2.2
 neighbor 10.0.0.1 remote-as 65001
 neighbor 20.0.0.2 remote-as 65003
 network 192.168.2.0 mask 255.255.255.0
 ```
> 🔹 R3 (AS 65003)
```py
router bgp 65003
 bgp router-id 3.3.3.3
 neighbor 20.0.0.1 remote-as 65002
 neighbor 30.0.0.1 remote-as 65004
 network 192.168.3.0 mask 255.255.255.0
```
> 🔹 R4 (AS 65004)
```py
router bgp 65004
 bgp router-id 4.4.4.4
 neighbor 30.0.0.2 remote-as 65003
 neighbor 40.0.0.2 remote-as 65001
 network 192.168.4.0 mask 255.255.255.0
```

#### 🔍 Verification Commands
```py
show ip bgp summary
show ip bgp
show ip route bgp
```


