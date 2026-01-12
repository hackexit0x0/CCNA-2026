# 🔵 OSPF (Open Shortest Path First)

## 📘 What is OSPF?
OSPF (Open Shortest Path First) is a **link-state interior gateway routing protocol (IGP)** used to exchange routing information **within a single autonomous system (AS)**.

OSPF is an **open standard protocol** and is widely used in **enterprise and service provider networks** due to its **fast convergence and scalability**.

---

## ⚙️ How OSPF Works (Simple Flow)
1. Routers discover neighbors using **Hello packets**
2. Neighbor adjacencies are formed
3. Routers exchange **Link-State Advertisements (LSAs)**
4. All routers build the same **Link-State Database (LSDB)**
5. **SPF (Dijkstra) algorithm** calculates the shortest path
6. Best routes are installed in the routing table

---

## 🧭 OSPF Areas
OSPF uses a **hierarchical area design** to improve scalability.

### 🔹 Area 0 (Backbone Area)
- Central area of OSPF
- All other areas must connect to Area 0

### 🔹 Non-Backbone Areas
- Used to reduce routing overhead
- Examples: Standard Area, Stub Area, Totally Stubby Area, NSSA

---

## 📦 OSPF Transport Details
- Uses **IP protocol number 89**
- Does **not use TCP or UDP**
- Multicast addresses:
  - **224.0.0.5** → All OSPF Routers
  - **224.0.0.6** → DR/BDR Routers

---

## 📏 Metric Used in OSPF
- Metric = **Cost**
- Cost is based on **bandwidth**
- Formula:


### Cost = Reference Bandwidth / Interface Bandwidth

- Lower cost = better path

---

## 🧠 OSPF Router Types
- **Internal Router**
- **Backbone Router**
- **ABR (Area Border Router)**
- **ASBR (Autonomous System Boundary Router)**

---

## 👑 DR & BDR (Designated Router)
- Used in **multi-access networks** (like Ethernet)
- Reduces LSA flooding
- Election based on:
  1. OSPF Priority
  2. Router ID

---

## 🔄 OSPF Packet Types
1. Hello
2. Database Description (DBD)
3. Link-State Request (LSR)
4. Link-State Update (LSU)
5. Link-State Acknowledgment (LSAck)

---

## 🕒 OSPF Timers

| Timer | Default Value |
|------|--------------|
| Hello | 10 sec |
| Dead | 40 sec |

---

## 🛡️ Loop Prevention in OSPF
- Uses **LSDB synchronization**
- **SPF algorithm** ensures loop-free routing

---

## 🔐 Authentication in OSPF
- Plain text authentication
- MD5 authentication
- Secures routing updates

---

## ✅ Advantages of OSPF
- Fast convergence
- Highly scalable
- Open standard (multi-vendor support)
- Efficient bandwidth usage
- Supports VLSM and CIDR

---

## ❌ Disadvantages of OSPF
- Complex configuration
- Higher CPU and memory usage
- Requires careful area design

---

## 📌 Where OSPF is Used?
- Enterprise networks
- Large internal networks
- Service provider environments

---

## 🆚 OSPF vs RIP

| Feature | OSPF | RIP |
|------|------|------|
| Type | Link State | Distance Vector |
| Metric | Cost | Hop Count |
| Convergence | Fast | Slow |
| Scalability | High | Low |

---

## 🎯 Interview One-Line Answer
**OSPF is a link-state interior gateway routing protocol that uses the SPF algorithm and hierarchical areas to provide fast, scalable, and loop-free routing.**
