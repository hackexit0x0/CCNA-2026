# 🟣 EIGRP (Enhanced Interior Gateway Routing Protocol)

## 📘 What is EIGRP?
EIGRP (Enhanced Interior Gateway Routing Protocol) is a **Cisco-developed advanced distance vector routing protocol** (often called a **hybrid protocol**).

It is used to exchange routing information **within the same autonomous system (AS)** and provides **fast convergence and high scalability**.

---

## ⚙️ How EIGRP Works (Simple Flow)
1. Routers discover neighbors using **Hello packets**
2. Neighbor relationships are established
3. Routers exchange routing information
4. EIGRP calculates the **best path using metrics**
5. Changes are updated **only when needed**

---

## 📦 EIGRP Transport Details
- Uses **IP protocol number 88** (not TCP/UDP)
- Multicast address: **224.0.0.10**
- Reliable transport using **RTP (Reliable Transport Protocol)**

---

## 📏 Metric Used in EIGRP
EIGRP uses a **composite metric**, mainly based on:

- **Bandwidth**
- **Delay**

(Optional but disabled by default)
- Load
- Reliability

### Default Metric Formula (Simplified)

---

## 🚀 Key EIGRP Feature – DUAL Algorithm
EIGRP uses **DUAL (Diffusing Update Algorithm)** to:
- Calculate loop-free routes
- Provide **instant failover**
- Ensure fast convergence

---

## 🧭 EIGRP Route Types
- **Successor** – Best path
- **Feasible Successor** – Backup path (loop-free)

---

## 🔄 EIGRP Tables
1. **Neighbor Table** – Stores neighboring routers
2. **Topology Table** – Stores all learned routes
3. **Routing Table** – Stores best routes only

---

## 🕒 EIGRP Timers

| Timer | Default Value |
|------|--------------|
| Hello | 5 sec (LAN) |
| Hold | 15 sec |

---

## 🔐 Authentication in EIGRP
- Supports **MD5 authentication**
- Prevents unauthorized routing updates

---

## ✅ Advantages of EIGRP
- Very fast convergence
- Scalable for large networks
- Uses bandwidth efficiently
- Supports VLSM and CIDR
- Loop-free routing

---

## ❌ Disadvantages of EIGRP
- Originally Cisco proprietary (limited vendor support)
- More complex than RIP
- Not ideal for multi-vendor environments

---

## 🔁 Loop Prevention in EIGRP
- Uses **DUAL algorithm**
- Maintains feasible successors
- Ensures loop-free paths automatically

---

## 📌 Where EIGRP is Used?
- Cisco-based enterprise networks
- Large internal networks
- Data centers

---

## 🆚 EIGRP vs Other Routing Protocols

| Feature | EIGRP | RIP | OSPF |
|------|------|------|------|
| Type | Hybrid | Distance Vector | Link State |
| Metric | Bandwidth + Delay | Hop Count | Cost |
| Convergence | Very Fast | Slow | Fast |
| Scalability | High | Low | High |

---

## 🎯 Interview One-Line Answer
**EIGRP is a Cisco-developed hybrid routing protocol that uses the DUAL algorithm to provide fast, loop-free routing with metrics based on bandwidth and delay.**
