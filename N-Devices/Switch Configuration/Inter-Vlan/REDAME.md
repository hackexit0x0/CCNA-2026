# 📘 Inter-VLAN Routing – Short Notes (CCNA Friendly)

---

#### 🔹 What is Inter-VLAN Routing?
**Inter-VLAN Routing** is a method that allows **devices in different VLANs to communicate with each other** using a **Layer 3 device** (Router or Layer 3 Switch).

👉 By default, VLANs are **isolated** and **cannot communicate**.

---

#### 🔹 Why Inter-VLAN is Needed?
- VLANs create **separate broadcast domains**
- Communication between departments/networks is required
- Inter-VLAN enables **controlled & secure communication**

---

#### 🔹 Types of Inter-VLAN Routing

##### 1️⃣ Router-on-a-Stick (RoAS)
- Uses **one router interface**
- Creates **sub-interfaces**
- Switch port works as **trunk**

✅ Cost-effective  
❌ Slower (router-based)

---

##### 2️⃣ Layer 3 Switch (SVI Method) ⭐
- Uses **SVI (Switch Virtual Interface)**
- Routing done inside switch
- No external router needed

✅ Fast  
✅ Scalable  
❌ Costly

---

##### 3️⃣ Legacy Inter-VLAN Routing (Old)
- One router interface per VLAN
- Not scalable
- Rarely used today

❌ Not recommended

---

#### 🔹 How Inter-VLAN Routing Works (Simple)
1. PC in VLAN 10 sends packet to VLAN 20  
2. Packet goes to **default gateway**
3. Layer 3 device checks routing table
4. Packet forwarded to destination VLAN

👉 Routing happens at **Layer 3 (Network Layer)**

---

#### 🔹 Advantages of Inter-VLAN Routing
- ✔ Enables communication between VLANs
- ✔ Better network segmentation
- ✔ Improved security
- ✔ Reduced broadcast traffic
- ✔ Efficient IP management

---

#### 🔹 Disadvantages of Inter-VLAN Routing
- ❌ Router-on-a-Stick can be slow
- ❌ Misconfiguration can cause security risks
- ❌ Layer 3 switches are expensive
- ❌ Requires proper planning

---

#### 🔹 Real-Life Example
- VLAN 10 → HR Department  
- VLAN 20 → Finance Department  
- VLAN 30 → IT Department  

Inter-VLAN allows HR to access Finance servers **through routing rules**.

---

#### 🔹 One-Line Exam Definition
> **Inter-VLAN routing allows communication between different VLANs using a Layer 3 device.**

---

#### 🔹 Comparison Table

| Method | Device Used | Speed | Cost |
|------|------------|------|------|
| Router-on-a-Stick | Router | Medium | Low |
| Layer 3 Switch | L3 Switch | High | High |
| Legacy | Router | Low | Low |

---

#### ✅ CCNA Tip
- **Small network** → Router-on-a-Stick  
- **Enterprise network** → Layer 3 Switch (SVI)

---
