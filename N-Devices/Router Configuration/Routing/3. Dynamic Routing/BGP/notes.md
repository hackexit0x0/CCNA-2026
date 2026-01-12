# 🔵 BGP (Border Gateway Protocol)

## 📘 What is BGP?
BGP (Border Gateway Protocol) is a **path vector routing protocol** used to exchange routing information **between different autonomous systems (AS)** on the Internet.

BGP is the **core routing protocol of the Internet** and is mainly used by **ISPs and large organizations**.

---

## 🌐 What is an Autonomous System (AS)?
An **Autonomous System (AS)** is a collection of IP networks and routers under the control of a single organization.

- Each AS has a **unique AS Number (ASN)**
- Example: ISP, large company, cloud provider

---

## ⚙️ How BGP Works (Simple Flow)
1. BGP routers establish a **TCP connection**
2. Routers exchange routing information
3. Multiple paths to a destination are learned
4. BGP applies **path selection rules**
5. The **best path** is selected and installed in the routing table

---

## 🔗 BGP Transport Details
- Uses **TCP**
- Port number: **179**
- Reliable communication (no periodic full updates)

---

## 🧭 Metric Used in BGP
BGP does **not** use hop count.

Instead, it uses **path attributes** to select the best route.

### Common BGP Path Attributes:
- **AS_PATH** – Shortest AS path is preferred
- **NEXT_HOP** – Next router to reach destination
- **LOCAL_PREFERENCE** – Higher value preferred
- **MED (Multi-Exit Discriminator)** – Lower value preferred
- **ORIGIN** – IGP preferred over EGP

---

## 🧠 BGP Path Selection (Simplified Order)
1. Highest **Local Preference**
2. Shortest **AS_PATH**
3. Lowest **Origin type**
4. Lowest **MED**
5. eBGP preferred over iBGP
6. Lowest IGP cost to next hop

---

## 🔄 Types of BGP

### 1️⃣ eBGP (External BGP)
- Used **between different AS**
- Example: ISP ↔ ISP
- Default hop limit: 1

### 2️⃣ iBGP (Internal BGP)
- Used **within the same AS**
- Requires full mesh or route reflectors

---

## 🕒 BGP Timers

| Timer | Default Value |
|------|--------------|
| Keepalive | 60 sec |
| Hold Time | 180 sec |

---

## ✅ Advantages of BGP
- Highly **scalable**
- Very **stable**
- Policy-based routing
- Best for large networks and Internet routing

---

## ❌ Disadvantages of BGP
- Complex configuration
- Slow convergence
- Requires strong networking knowledge
- High memory usage in large tables

---

## 🔁 Loop Prevention in BGP
BGP prevents loops using:
- **AS_PATH attribute**
- If a router sees its own ASN in AS_PATH, it rejects the route

---

## 📌 Where BGP is Used?
- Internet backbone
- ISPs
- Data centers
- Large enterprise networks
- Cloud providers

---

## 🆚 BGP vs IGP Protocols (RIP / OSPF)

| Feature | BGP | RIP | OSPF |
|------|-----|-----|------|
| Type | Path Vector | Distance Vector | Link State |
| Metric | Path Attributes | Hop Count | Cost |
| Convergence | Slow | Slow | Fast |
| Scalability | Very High | Low | High |
| Usage | Internet / ISPs | Small Networks | Enterprise |

---

## 🎯 Interview One-Line Answer
**BGP is a path vector routing protocol used to exchange routing information between autonomous systems and is the backbone routing protocol of the Internet.**
