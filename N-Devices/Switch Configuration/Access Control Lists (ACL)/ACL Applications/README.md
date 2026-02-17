## ACL Applications on Switches (Layer 2 & Layer 3)
> ACLs (Access Control Lists) are used to control traffic flow for security, segmentation, and policy enforcement.

> We’ll cover:
+ Applying ACLs to VLANs
+ Applying ACLs to Ports
+ Applying ACLs to SVIs
+ Inbound vs Outbound direction
+ Security filtering best practices

### 1️⃣ Applying ACL to VLAN (VACL)
> 📘 VLAN ACL (VACL)

🔹 Purpose
+ Filters traffic within the same VLAN
+ Works at Layer 2
+ Can filter:
   + IP
   + ARP
   + Other non-IP traffic

🔹 Applied To:
> Entire VLAN (not interface)

> 🖥 Example
```py
Switch(config)# access-list 101 deny ip 192.168.10.0 0.0.0.255 any
Switch(config)# access-list 101 permit ip any any

Switch(config)# vlan access-map BLOCK_VLAN 10
Switch(config-access-map)# match ip address 101
Switch(config-access-map)# action drop

Switch(config)# vlan access-map BLOCK_VLAN 20
Switch(config-access-map)# action forward

Switch(config)# vlan filter BLOCK_VLAN vlan-list 10
```
✅ Used For:
  + Blocking host-to-host communication in same VLAN
  + Preventing lateral movement (security)

---

### 2️⃣ Applying ACL to Port (PACL)
> 📘 Port ACL (PACL)
🔹 Purpose
+ Filters traffic entering a physical Layer 2 interface
+ Controls what devices connected to that port can send

🔹 Applied To:

+ Physical interface (access or trunk port)

> 🖥 Example
```py
Switch(config)# access-list 50 deny 192.168.1.100 0.0.0.0
Switch(config)# access-list 50 permit any

Switch(config)# interface fa0/5
Switch(config-if)# ip access-group 50 in
```
> ⚠ Important

+ Filters only inbound traffic
+ Does NOT filter routed traffic (on L2 switch)
+ Does NOT filter switch-generated traffic

✅ Used For:

+ Restricting specific host
+ Controlling lab users
+ Basic endpoint security

---

### 3️⃣ Applying ACL to SVI (RACL)
> 📘 Router ACL (RACL on Layer 3 Switch)

🔹 Purpose

+ Filters traffic during inter-VLAN routing
+ Works like router ACL

🔹 Applied To:

+ SVI (interface vlan)
+ Routed physical port

> 🖥 Example
```py
Switch(config)# ip access-list extended BLOCK_HR
Switch(config-ext-nacl)# deny ip 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255
Switch(config-ext-nacl)# permit ip any any

Switch(config)# interface vlan 10
Switch(config-if)# ip access-group BLOCK_HR in
```
✅ Used For:

+ Blocking VLAN-to-VLAN access
+ Restricting department communication
+ Enforcing segmentation policy

### 4️⃣ ACL Direction: Inbound vs Outbound
> 📘 Traffic Direction

🔹 Inbound (in)

+ Filters traffic as it enters interface
> More efficient (drops early)
```py
ip access-group 100 in
```
🔹 Outbound (out)

+ Filters traffic as it leaves interface
```py
ip access-group 100 out
```
> 🧠 Rule of Thumb
```py
| ACL Type     | Placement        |
| ------------ | ---------------- |
| Standard ACL | Near destination |
| Extended ACL | Near source      |

```
---

### 5️⃣ Security Filtering Use Cases
+ 🔐 Common Security Applications
> ✅ 1. Block VLAN-to-VLAN Access

> Example:
+ HR VLAN cannot access Finance VLAN
+ Use Extended ACL on SVI

✅ 2. Block Specific Host
+ Use Standard ACL or PACL

✅ 3. Block Specific Application

> Example:
+ Block Telnet (TCP 23)
+ Allow HTTP (TCP 80)
```py
access-list 101 deny tcp any any eq 23
access-list 101 permit tcp any any eq 80
access-list 101 permit ip any any
```
✅ 4. Control Internet Access
+ Allow internal → Internet
+ Block Internet → Internal
+ Apply on edge SVI or routed interface

6️⃣ Quick Comparison
```py
| Application        | L2 Switch | L3 Switch |
| ------------------ | --------- | --------- |
| PACL (Port)        | ✅         | ✅         |
| VACL (VLAN)        | ✅         | ✅         |
| RACL (SVI)         | ❌         | ✅         |
| Inbound filtering  | ✅         | ✅         |
| Outbound filtering | Limited   | ✅         |

```

🧠 Best Practice Summary

+ ✔ Prefer Extended ACL for security
+ ✔ Apply close to source (extended)
+ ✔ Use inbound direction for efficiency
+ ✔ Always end ACL with permit ip any any (if needed)
+ ✔ Verify with:
```py
show access-lists
show ip interface
```

