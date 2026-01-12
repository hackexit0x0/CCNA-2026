# 🟠 IS-IS (Intermediate System to Intermediate System)

## 📘 What is IS-IS?
IS-IS (Intermediate System to Intermediate System) is a **link-state interior gateway routing protocol (IGP)** used to route packets **within a single autonomous system (AS)**.

It is commonly used by **ISPs and large service provider networks** because of its **high scalability and fast convergence**.

---

## 🌐 Key Terminology
- **Intermediate System (IS)** → Router  
- **End System (ES)** → Host / End device  

---

## ⚙️ How IS-IS Works (Simple Flow)
1. Routers discover neighbors using **Hello packets**
2. Adjacencies are formed
3. Routers exchange **Link-State Packets (LSPs)**
4. All routers build the same **Link-State Database (LSDB)**
5. **SPF (Dijkstra) algorithm** calculates the shortest path
6. Best routes are installed in the routing table

---

## 🧭 IS-IS Levels
IS-IS uses a **two-level hierarchy**:

### 🔹 Level 1 (L1)
- Routes **within the same area**
- Similar to OSPF intra-area routing

### 🔹 Level 2 (L2)
- Routes **between different areas**
- Similar to OSPF backbone routing

### 🔹 Level 1–2 Router
- Connects Level 1 areas to Level 2 backbone

---

## 📦 Transport Details
- Runs **directly over Layer 2**
- Does **not use TCP or UDP**
- Uses **CLNS** for routing information exchange

---

## 📏 Metric Used in IS-IS
- Uses **Cost** as the metric
- Lower cost = better path
- Default cost is based on interface configuration

---

## 🔄 IS-IS Addressing (NET)
IS-IS uses a **Network Entity Title (NET)** instead of IP addresses.

Example:
`49.0001.1921.6800.1001.00`


---

## 🕒 IS-IS Timers

| Timer | Default Value |
|------|--------------|
| Hello | 10 sec |
| Hold | 30 sec |
| LSP Lifetime | 1200 sec |

---

## 🛡️ Loop Prevention in IS-IS
- Uses **Link-State Database synchronization**
- **SPF algorithm** ensures loop-free paths

---

## 🔐 Authentication
- Supports **plain text and MD5 authentication**
- Secures routing updates

---

## ✅ Advantages of IS-IS
- Very scalable
- Fast convergence
- Stable for large networks
- Less CPU intensive than OSPF
- Ideal for service providers

---

## ❌ Disadvantages of IS-IS
- Complex configuration
- Harder to understand for beginners
- Less common in small enterprise networks

---

## 📌 Where IS-IS is Used?
- Internet Service Providers (ISPs)
- Large backbone networks
- Service provider core routing

---

## 🆚 IS-IS vs OSPF

| Feature | IS-IS | OSPF |
|------|------|------|
| Type | Link State | Link State |
| Layer | Layer 2 | Layer 3 |
| Areas | L1 / L2 | Area 0 |
| Scalability | Very High | High |
| Usage | ISPs | Enterprises |

---

## 🎯 Interview One-Line Answer
**IS-IS is a link-state interior gateway routing protocol that uses a two-level hierarchy and SPF algorithm to provide fast, scalable routing, commonly used in service provider networks.**
