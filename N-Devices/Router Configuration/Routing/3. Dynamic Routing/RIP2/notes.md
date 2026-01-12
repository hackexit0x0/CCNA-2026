# 🟢 RIPv2 (Routing Information Protocol Version 2)

## 📘 What is RIPv2?
RIPv2 (Routing Information Protocol Version 2) is an **enhanced version of RIPv1**.  
It is a **distance vector routing protocol** that uses **hop count** as its routing metric.

RIPv2 overcomes many limitations of RIPv1 by adding **classless routing, authentication, and multicast updates**.

---

## ⚙️ How RIPv2 Works
1. Routers exchange routing information with neighboring routers
2. Updates are sent every **30 seconds**
3. Routing decisions are based on **lowest hop count**
4. Supports subnet masks with route updates
5. Routing tables update automatically

---

## 📏 Metric Used in RIPv2

### 🔢 Hop Count
- **Hop** = one router
- Lower hop count = better route

### ❗ Maximum Hop Count
- **15 hops** → Reachable
- **16 hops** → Unreachable (Infinity)

➡️ Suitable only for **small networks**

---

## 🆕 Improvements Over RIPv1
- Supports **VLSM (Variable Length Subnet Mask)**
- Supports **CIDR**
- Includes **subnet mask** in routing updates
- Supports **authentication**
- Uses **multicast instead of broadcast**

---

## 📦 Transport & Communication Details
- Uses **UDP**
- Port number: **520**
- Multicast address: **224.0.0.9**
- Update interval: **30 seconds**

---

## 🔐 Authentication in RIPv2
RIPv2 supports route authentication to prevent unauthorized routing updates.

### Types of Authentication:
- Plain Text Authentication
- MD5 Authentication (More secure)

---

## 🛡️ Loop Prevention Techniques
RIPv2 uses the same loop prevention mechanisms as RIPv1:

- **Split Horizon**
- **Route Poisoning**
- **Poison Reverse**
- **Hold-Down Timer**

---

## 🕒 RIPv2 Timers

| Timer       | Value |
|------------|-------|
| Update     | 30 sec |
| Invalid    | 180 sec |
| Hold-down  | 180 sec |
| Flush      | 240 sec |

---

## ✅ Advantages of RIPv2
- Simple and easy to configure
- Supports VLSM and CIDR
- Authentication improves security
- Low CPU and memory usage

---

## ❌ Disadvantages of RIPv2
- Maximum hop count limited to 15
- Slow convergence
- Not scalable for large networks
- Periodic full routing table updates

---

## 📌 Where RIPv2 is Used?
- Small enterprise networks
- Lab environments
- Learning and training
- ❌ Not suitable for large or enterprise-scale networks

---

## 🆚 RIPv1 vs RIPv2

| Feature | RIPv1 | RIPv2 |
|------|------|------|
| Routing Type | Classful | Classless |
| VLSM Support | ❌ No | ✅ Yes |
| Authentication | ❌ No | ✅ Yes |
| Update Method | Broadcast | Multicast |
| Subnet Mask | ❌ No | ✅ Yes |

---

## 🎯 Interview One-Line Answer
**RIPv2 is a classless distance vector routing protocol that uses hop count as a metric, supports VLSM, CIDR, and authentication, and uses multicast for routing updates.**
