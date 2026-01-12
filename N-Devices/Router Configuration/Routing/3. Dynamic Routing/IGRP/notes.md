# 🔴 IGRP (Interior Gateway Routing Protocol)

## 📘 What is IGRP?
IGRP (Interior Gateway Routing Protocol) is a **Cisco proprietary distance vector routing protocol** used to exchange routing information **within an autonomous system (AS)**.

IGRP was designed to **overcome the limitations of RIP**, especially the **15-hop limit**, and is now **obsolete**, replaced by **EIGRP**.

---

## ⚙️ How IGRP Works (Simple Flow)
1. Routers share routing information with neighboring routers
2. Updates are sent periodically
3. Routers calculate the best path using multiple metrics
4. Best route is added to the routing table
5. Routing tables are updated automatically

---

## 📦 IGRP Transport Details
- Uses **IP protocol number 9**
- Does **not use TCP or UDP**
- Sends periodic updates

---

## 📏 Metric Used in IGRP
IGRP uses a **composite metric**, unlike RIP.

### Metrics Used:
- **Bandwidth**
- **Delay**
- **Load**
- **Reliability**
- **MTU**

➡️ This allows more accurate route selection than hop count.

---

## ❗ Maximum Hop Count
- Default maximum hop count: **100**
- Maximum configurable hop count: **255**

➡️ Much better than RIP but still limited compared to modern protocols.

---

## 🔄 Update Interval
- Routing updates are sent every **90 seconds**
- Slower convergence than modern protocols

---

## 🕒 IGRP Timers

| Timer | Value |
|------|------|
| Update | 90 sec |
| Invalid | 270 sec |
| Hold-down | 280 sec |
| Flush | 630 sec |

---

## 🛡️ Loop Prevention Techniques
IGRP uses classic distance-vector loop prevention methods:
- **Split Horizon**
- **Route Poisoning**
- **Hold-Down Timers**

---

## ✅ Advantages of IGRP
- Better metric selection than RIP
- Supports larger networks than RIP
- Stable for its time

---

## ❌ Disadvantages of IGRP
- Cisco proprietary
- Classful (no VLSM or CIDR support)
- Slow convergence
- Obsolete and no longer supported

---

## 📌 Where IGRP is Used?
- Legacy Cisco networks
- Historical study and learning
- ❌ Not used in modern networks

---

## 🔁 IGRP vs EIGRP

| Feature | IGRP | EIGRP |
|------|------|------|
| Type | Distance Vector | Hybrid |
| Metric | Composite | Bandwidth + Delay |
| VLSM Support | ❌ No | ✅ Yes |
| Convergence | Slow | Very Fast |
| Status | Obsolete | Active |

---

## 🎯 Interview One-Line Answer
**IGRP is a Cisco proprietary distance vector routing protocol that uses multiple metrics for path selection and was designed to improve RIP but is now obsolete and replaced by EIGRP.**
