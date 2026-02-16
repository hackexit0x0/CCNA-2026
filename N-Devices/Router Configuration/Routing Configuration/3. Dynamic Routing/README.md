### DYNAMIC ROUTING
> Advantages of Dynamic over static:> 
>There is no need to know the destination networks.\
>Need to advertise the directly connected networks.\
>Updates the topology changes dynamically.\
>Administrative work is reduced\
>Used for large organizations.\
>Neighbor routers exchange routing information and build the routing table automatically.

> Types of Dynamic Routing Protocols> 
>Distance Vector Protocol\
>Link State Protocol\
>Hybrid Protocol\

---
| **Distance Vector Protocol** | **Link State Protocol** | **Hybrid Protocol** |
|-----------------------------|------------------------|---------------------|
| Works with Bellman-Ford algorithm | Works with Dijkstra algorithm | Also called Advanced Distance Vector Protocol |
| Periodic updates | Link-state updates | Works with DUAL algorithm |
| Classful routing protocol | Classless routing protocol | Link-state updates |
| Full routing tables are exchanged | Missing routes are exchanged | Classless routing protocol |
| Updates are through broadcast | Updates are through multicast | Missing routes are exchanged |
| Examples: RIP v1, RIP v2, IGRP | Examples: OSPF, IS-IS | Updates are through multicast |
| — | — | Example: EIGRP |
---

>  Administrative Distance
```py
• Rating of the Trustworthiness of a routing information source.
• The Number is between 0 and 255
• The higher the value, the lower the trust.
• Default administrative distances are as follows :
       • Directly Connected = 0
       • Static Route = 1
       • IGRP = 100
       • OSPF = 110
       • RIP = 120
       • EIGRP = 90/170
```


## Quick Comparison

| Protocol | Type            | Metric    | Convergence | Scalability | Classless |
| -------- | --------------- | --------- | ----------- | ----------- | --------- |
| RIPv1    | Distance Vector | Hop Count | Slow        | Small       | ❌         |
| RIPv2    | Distance Vector | Hop Count | Slow        | Small       | ✅         |
| IGRP     | Distance Vector | Composite | Slow        | Medium      | ❌         |
| OSPF     | Link State      | Cost      | Fast        | Large       | ✅         |
| IS-IS    | Link State      | Cost      | Fast        | Very Large  | ✅         |
| EIGRP    | Hybrid          | Composite | Very Fast   | Large       | ✅         |
| BGP      | Path Vector     | Policy    | Slow        | Internet    | ✅         |

---

### 📌 What is Dynamic Routing?

#### 🔰 Definition
> **Dynamic Routing** is a routing mechanism where routers **automatically learn, update, and maintain routes** using routing protocols.  

> Routers exchange routing information with neighbors and update routing tables whenever the network topology changes.

### ✅ Why Dynamic Routing?
- No manual route configuration
- Automatic topology updates
- Fault tolerance
- High scalability
- Suitable for medium and large networks

---

#### 🔁 Static Routing vs Dynamic Routing

| Feature | Static Routing | Dynamic Routing |
|------|---------------|----------------|
| Manual Configuration | Yes | No |
| Automatic Updates | No | Yes |
| Scalability | Low | High |
| Fault Tolerance | No | Yes |
| Complexity | Low | High |
| Best Use | Small networks | Large networks |

---

### 🔹 Administrative Distance (AD)

Administrative Distance defines the **trustworthiness** of a routing source.  
Lower value = higher priority.

| Route Source | AD |
|------------|----|
| Connected | 0 |
| Static | 1 |
| EIGRP | 90 |
| OSPF | 110 |
| RIP | 120 |
| eBGP | 20 |
| iBGP | 200 |

---

## 1️⃣ Distance Vector Protocols

### 📌 Definition
Distance Vector protocols calculate routes based on:
- Distance (metric)
- Direction (next-hop router)

Routers periodically share **entire routing tables** with neighbors.

### 🧠 Algorithm
- Bellman-Ford Algorithm

### ✅ Advantages
- Easy to configure
- Low CPU and memory usage
- Suitable for small networks

### ❌ Disadvantages
- Slow convergence
- Routing loops possible
- Limited scalability
- Periodic full updates increase traffic

### 📘 Examples
- RIP (RIPv1, RIPv2)
- IGRP (obsolete)

---

## 2️⃣ Link State Protocols

### 📌 Definition
Link State protocols build a **complete topology map** of the network and calculate the shortest path.

### 🧠 Algorithm
- Dijkstra (SPF) Algorithm

### ✅ Advantages
- Very fast convergence
- Highly scalable
- Loop-free routing
- Efficient updates (only changes)

### ❌ Disadvantages
- High CPU and memory usage
- Complex configuration
- Requires planning

### 📘 Examples
- OSPF
- IS-IS

---

## 3️⃣ Hybrid Routing Protocols

### 📌 Definition
Hybrid protocols combine the features of:
- Distance Vector
- Link State

### 🧠 Algorithm
- DUAL (Diffusing Update Algorithm)

### ✅ Advantages
- Very fast convergence
- Loop-free design
- Efficient bandwidth usage
- Supports VLSM and CIDR

### ❌ Disadvantages
- Mostly Cisco proprietary
- Complex metric calculation

### 📘 Example
- EIGRP

---

## 4️⃣ Path Vector Protocols

### 📌 Definition
Path Vector protocols make routing decisions based on **path attributes and policies**, not hop count.

### ✅ Advantages
- Extremely scalable
- Policy-based routing
- Ideal for Internet routing

### ❌ Disadvantages
- Very complex configuration
- Slow convergence
- Difficult troubleshooting

### 📘 Example
- BGP

---

## 🏢 IGP vs EGP

| Type | Description | Protocols |
|----|-----------|----------|
| IGP | Routing within one AS | RIP, OSPF, EIGRP, IS-IS |
| EGP | Routing between AS | BGP |

---

## 📦 Classful vs Classless Routing

### ❌ Classful Protocols
- Do not send subnet mask
- No VLSM or CIDR support

**Examples:** RIPv1, IGRP

### ✅ Classless Protocols
- Include subnet mask
- Support VLSM and CIDR

**Examples:** RIPv2, OSPF, EIGRP, IS-IS, BGP

---

## 🚀 Individual Protocol Overview

---

## 🟢 RIP (Routing Information Protocol)

### Definition
RIP is a **distance vector protocol** that uses **hop count** as its metric.

### Advantages
- Very simple
- Easy configuration
- Low resource usage

### Disadvantages
- Max hop count = 15
- Slow convergence
- Not scalable
- Loop issues

---

## 🔵 OSPF (Open Shortest Path First)

### Definition
OSPF is a **link-state protocol** using the **SPF algorithm**.

### Advantages
- Fast convergence
- Highly scalable
- Hierarchical design
- Industry standard

### Disadvantages
- Complex configuration
- Higher CPU and memory usage

---

## 🟠 EIGRP (Enhanced IGRP)

### Definition
EIGRP is a **hybrid routing protocol** developed by Cisco.

### Advantages
- Very fast convergence
- Loop-free
- Efficient updates

### Disadvantages
- Cisco-centric
- Proprietary features

---

## 🔴 BGP (Border Gateway Protocol)

### Definition
BGP is a **path vector protocol** used on the **Internet**.

### Advantages
- Massive scalability
- Policy control
- Stable routing

### Disadvantages
- Very complex
- Slow convergence
- Hard to troubleshoot

---

## 📊 Quick Comparison Table

| Protocol | Type | Metric | Convergence | Scalability |
|--------|-----|-------|------------|------------|
| RIP | Distance Vector | Hop Count | Slow | Small |
| OSPF | Link State | Cost | Fast | Large |
| EIGRP | Hybrid | Composite | Very Fast | Large |
| BGP | Path Vector | Policy | Slow | Internet |

---

## 🎯 Exam & Interview Focus

- Difference between RIP, OSPF, EIGRP, and BGP
- Administrative Distance
- Metric types
- IGP vs EGP
- Classful vs Classless
- Convergence and routing loops

---

## 📌 Conclusion

Dynamic routing protocols provide **automation, scalability, and fault tolerance**.  
Understanding their **behavior, metrics, and use cases** is essential for **network engineers and cybersecurity professionals**.

---

### 📚 References
- Zenarmor Networking Guide
- Cisco Documentation
- CCNA Routing Concepts
