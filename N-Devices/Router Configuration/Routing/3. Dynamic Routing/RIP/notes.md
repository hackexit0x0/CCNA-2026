# 🟢 RIP (Routing Information Protocol)

## 📘 What is RIP?
RIP (Routing Information Protocol) is a **dynamic routing protocol** used to automatically find the best path between networks.

It is a **Distance Vector Routing Protocol**, which means:
- Routers share routing information with neighboring routers
- Routing decisions are based on **distance (hop count)**

---

## ⚙️ How RIP Works (Simple Flow)
1. Each router sends its **routing table** to neighboring routers
2. Updates are sent every **30 seconds**
3. Routers compare available routes
4. The route with the **lowest hop count** is selected
5. Routing tables are updated automatically

---

## 📏 Metric Used in RIP

### 🔢 Hop Count
- **Hop** = one router
- Path with fewer routers is considered the **best path**

### ❗ Maximum Hop Count
- **15 hops** → Reachable
- **16 hops** → Unreachable (Infinity)

➡️ This limitation makes RIP suitable only for **small networks**

---

## 🔄 RIP Versions

### 1️⃣ RIPv1
- Classful routing protocol
- Does **not support VLSM**
- No authentication
- Uses **broadcast** (255.255.255.255)

### 2️⃣ RIPv2
- Classless routing protocol
- Supports **VLSM & CIDR**
- Supports **authentication**
- Uses **multicast** (224.0.0.9)

---

## 📦 RIP Transport Details
- Uses **UDP**
- Port number: **520**
- Update interval: **30 seconds**

---

## ✅ Advantages of RIP

### 1️⃣ Very Simple
- Easy to understand
- Ideal for beginners

### 2️⃣ Easy Configuration
- Requires very few commands
- Minimal setup effort

### 3️⃣ Low Resource Usage
- Uses less CPU and memory
- Works well on older routers

---

## ❌ Disadvantages of RIP

### 1️⃣ Maximum Hop Count = 15
- Not suitable for large networks
- Networks beyond 15 routers are unreachable

### 2️⃣ Slow Convergence
- Takes time to adapt to network changes
- Slow recovery after link failure

### 3️⃣ Not Scalable
- Sends full routing table updates frequently
- Poor performance in large networks

### 4️⃣ Loop Issues
- Routing loops can occur due to incorrect routing information

---

## 🔁 Routing Loop Problem (Example)
- Network path: **Router A → Router B → Router C**
- Link between **B and C fails**
- Router B informs A that C is unreachable
- Router A still believes C is reachable via B
- This creates a **routing loop**

---

## 🛡️ Loop Prevention Techniques in RIP

### 🔹 Split Horizon
- Prevents sending route updates back to the router from which they were learned

### 🔹 Route Poisoning
- Marks failed routes with hop count **16**

### 🔹 Hold-Down Timer
- Temporarily ignores unstable route updates

### 🔹 Poison Reverse
- Explicitly advertises unreachable routes back to neighbors

---

## 🕒 RIP Timers

| Timer       | Value |
|------------|-------|
| Update     | 30 sec |
| Invalid    | 180 sec |
| Hold-down  | 180 sec |
| Flush      | 240 sec |

---

## 📌 Where RIP is Used?
- Small networks
- Lab environments
- Learning and practice
- ❌ Not recommended for enterprise networks

---

## 🆚 RIP vs Other Routing Protocols

| Feature       | RIP | OSPF | EIGRP |
|--------------|-----|------|-------|
| Type         | Distance Vector | Link State | Hybrid |
| Metric       | Hop Count | Cost | Bandwidth + Delay |
| Convergence  | Slow | Fast | Very Fast |
| Scalability  | Low | High | High |

---

## 🎯 Interview One-Line Answer
**RIP is a distance vector routing protocol that uses hop count as a metric with a maximum limit of 15 hops, making it suitable only for small networks.**
