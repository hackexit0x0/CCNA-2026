### 🔀 Inter-VLAN Routing (Layer 3 Switch & Router)
#### 📌 What is Inter-VLAN Routing?

> Inter-VLAN Routing is the process that allows devices in different VLANs to communicate with each other using a Layer 3 device (L3 Switch or Router).

> 👉 Since each VLAN is a separate broadcast domain, communication between them cannot happen without routing.

### [Layer 3 Switch](L3switch.md)
> 🧠 Devices Used for Inter-VLAN Routing
#### 🔹 **Definition:** Layer 3 Switch (L3 Switch)
> A Layer 3 Switch is a network switch that can perform routing functions in addition to normal switching.

✅ Key Points
- Works at Layer 2 + Layer 3
- Uses SVIs (Switched Virtual Interfaces) → `interface vlan X`
- Performs Inter-VLAN Routing internally
- Routing is hardware-based (ASIC) → very fast
- Acts as default gateway for VLANs

📌 Simple Definition (Exam-ready)
> A Layer 3 Switch is a switch that can route traffic between VLANs using SVIs, without needing an external router.

### [Router](Router.md)
#### 🔹 **Definition:** Router (Router-on-a-Stick)
> A Router is a Layer 3 device that connects different networks and routes traffic between them.

> When used for VLANs, it uses Router-on-a-Stick, where:

- One physical interface
- Multiple sub-interfaces
- Connected to switch via trunk link

✅ Key Points
- Works at Layer 3 only
- Uses sub-interfaces → `fa0/0.10, fa0/0.20`
- Routing is software-based
- Single trunk link → possible bottleneck
- Common in small networks / labs

📌 Simple Definition (Exam-ready)
> A Router performs Inter-VLAN Routing using sub-interfaces over a trunk link, known as Router-on-a-Stick.

🆚 Difference Between Layer 3 Switch and Router
---
| Feature         | Layer 3 Switch          | Router            |
| --------------- | ----------------------- | ----------------- |
| OSI Layer       | Layer 2 + 3             | Layer 3           |
| Routing Method  | SVI (interface vlan X)  | Sub-interfaces    |
| Routing Speed   | Very Fast (Hardware)    | Slower (Software) |
| Trunk Link      | Not mandatory           | Mandatory         |
| Bottleneck      | ❌ No                    | ✅ Yes             |
| Scalability     | High                    | Low–Medium        |
| Best Use Case   | Enterprise / Campus LAN | Small networks    |
| Default Gateway | SVI IP                  | Sub-interface IP  |
---

#### 📝 One-Line Exam Notes (Very Important)
- L3 Switch → Uses SVIs + ip routing
- Router → Uses sub-interfaces + trunk
- SVI IP / Router IP = Default Gateway for PCs
- Without routing → VLANs cannot communicate
- If you want next, I can give:
- Short exam answers (1–2 lines)
- Interview Q&A
- Diagram explanation (step-by-step)
- Troubleshooting notes