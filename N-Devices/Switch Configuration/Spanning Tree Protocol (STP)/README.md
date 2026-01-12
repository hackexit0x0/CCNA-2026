### Spanning Tree Protocol (STP)

#### 🔹 What is STP?
+ <a href="https://youtu.be/aIG38PMoSBA?si=jbP_D-e9fwdM75Qe">Youtube STP Working</a>


> **Spanning Tree Protocol (STP)** is a **Layer 2 protocol** that prevents network loops in Ethernet networks by blocking redundant paths.

- **Standard:** IEEE 802.1D Code
- **Used in:** Switches  
- **Purpose:** Prevents broadcast storms  
- **Result:** Ensures loop-free topology  

### STP Path Cost Table (Classic IEEE 802.1D)
> 🔷 Link Bandwidth vs STP Cost

| Link Bandwidth | STP Cost |
| -------------- | -------- |
| 4 Mbps         | 250      |
| 10 Mbps        | 100      |
| 16 Mbps        | 62       |
| 45 Mbps        | 39       |
| **100 Mbps**   | **19** ⭐ |
| 155 Mbps       | 14       |
| 622 Mbps       | 6        |
| 1 Gbps         | 4        |
| 10 Gbps        | 2        |

---

#### 🔹 Why STP is Required?
Without STP:
- ❌ Broadcast storms  
- ❌ MAC address table instability  
- ❌ Duplicate frames  
- ❌ Complete network failure  

---

### 🔸 Enabling / Disabling STP
>  ✅ Enable STP (Default – Usually already enabled)
```py
Switch(config)# spanning-tree vlan 1
```

> ❌ Disable STP (NOT Recommended)
```py
Switch(config)# no spanning-tree vlan 1
```
> ⚠️ **Warning:** Disabling STP can cause loops and crash the network.

---

### 🔸 Selecting Root Bridge
---

###  🔹 Root Bridge Definition

> The **Root Bridge** is the main switch in the STP topology.  
> All STP path calculations start from the root bridge.

>  🏆 How Root Bridge is Selected?
- Lowest **Bridge ID**
- Bridge ID = **Priority + MAC Address**

>  ✅ Set Switch as Root Bridge
```py
Switch(config)# spanning-tree vlan 1 priority 4096

#### OR (Recommended)

Switch(config)# spanning-tree vlan 1 root primary
```

> ❌ Set Backup Root
```py
Switch(config)# spanning-tree vlan 1 root secondary
```

### ✔ Advantages
- Predictable network design  
- Faster convergence  
- Controlled traffic flow  

### ❌ Disadvantages
- Misconfiguration may cause outage  
- Requires proper planning  



### 🔸 PortFast
---

#### 🔹 PortFast Definition
> **PortFast** allows a port to skip listening & learning states and go directly to forwarding.

> 📌 Used on **end-device ports** (PC, Laptop, Printer)

#### ✅ Enable PortFast (Interface Mode)
```py
Switch(config)# interface fa0/1
Switch(config-if)# spanning-tree portfast
```

#### ✅ Global PortFast (All Access Ports)
```py
Switch(config)# spanning-tree portfast default
```

#### ✔ Advantages
- Fast host connectivity  
- No boot delay  
- Ideal for PCs  

#### ❌ Disadvantages
- Loop risk if used on switch-to-switch links  



### 🔸 BPDU Guard
----

### 🔹 BPDU Guard Definition
> **BPDU Guard** shuts down the port if a BPDU is received.

> 📌 Protects **PortFast ports**

#### ✅ Enable BPDU Guard (Interface)
```py
Switch(config-if)# spanning-tree bpduguard enable
```

#### ✅ Global BPDU Guard
```py
Switch(config)# spanning-tree portfast bpduguard default
```

### ✔ Advantages
- Prevents accidental loops  
- Strong security  
- Automatic protection  

### ❌ Disadvantages
- Port may go **err-disabled**  
- Needs manual recovery  

---

### 🔸 BPDU Filter
>  🔹 BPDU Filter Definition
> **BPDU Filter** blocks sending and receiving BPDUs.

> ⚠️ Very dangerous if misused

#### ✅ Enable BPDU Filter (Interface)
```py
Switch(config-if)# spanning-tree bpdufilter enable
```

#### ✅ Global BPDU Filter
```py
Switch(config)# spanning-tree portfast bpdufilter default
```

#### ✔ Advantages
- Reduces STP traffic  
- Useful for special test cases  

#### ❌ Disadvantages
- High loop risk  
- Not recommended in production  

---

### 🔸 Loop Guard
> 🔹 Loop Guard Definition
> **Loop Guard** prevents loops caused by missing BPDUs on non-designated ports.

> 📌 Used on **switch-to-switch links**

#### ✅ Enable Loop Guard (Interface)
```py
Switch(config-if)# spanning-tree guard loop
```

#### ✅ Global Loop Guard
```py
Switch(config)# spanning-tree loopguard default
```

### ✔ Advantages
- Prevents unidirectional link loops  
- Improves network stability  

### ❌ Disadvantages
- Slight delay in recovery  
- Extra configuration required  

---

### 🔸 Root Guard

> 🔹 Root Guard Definition
> **Root Guard** prevents another switch from becoming the Root Bridge.

> 📌 Used on **downstream ports**

#### ✅ Enable Root Guard
```py
Switch(config-if)# spanning-tree guard root
```

#### ✔ Advantages
- Protects root bridge position  
- Prevents topology change  
- Improves control  

#### ❌ Disadvantages
- Port may go **root-inconsistent**  
- Requires proper design  

---

#### 📌 STP Feature Comparison Table

| Feature      | Purpose                     | Used On          |
|--------------|-----------------------------|------------------|
| PortFast     | Fast forwarding             | End devices      |
| BPDU Guard   | Shutdown on BPDU            | Access ports     |
| BPDU Filter  | Block BPDUs                 | Special cases    |
| Loop Guard   | Prevent missing BPDU loops  | Trunk links      |
| Root Guard   | Protect root bridge         | Downstream ports |

---

## 🧠 Exam Tip (CCNA)
- **PortFast + BPDU Guard = Best Practice**
- ❌ Never use PortFast on trunk ports  
- **Root Guard ≠ Loop Guard**
