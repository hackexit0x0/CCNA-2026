### EtherChannel / Link Aggregation (README.md)

#### What is EtherChannel?
> EtherChannel is a technology used to **bundle multiple physical Ethernet links into one logical link**.  
> It increases **bandwidth**, provides **redundancy**, and enables **load balancing**.

### Types of EtherChannel
+ [1. LACP (Link Aggregation Control Protocol)](#)
+ [2. PAgP (Port Aggregation Protocol)](#)
+ [3. ](#)

---

### 1. LACP (Link Aggregation Control Protocol)

+ Definition
> LACP is an **IEEE standard (802.3ad / 802.1AX)** protocol that automatically negotiates and manages EtherChannel links between devices.

> Modes
- **Active** → Actively sends LACP packets
- **Passive** → Listens for LACP packets only

> Configuration Commands
```py
Switch(config)#interface range gig0/1-2
Switch(config-if-range)#switchport mode trunk
Switch(config-if-range)#channel-group 1 mode active
```
> Verification
```py
Switch#show etherchannel summary
Switch#show lacp neighbor

```
---
### 2. PAgP (Port Aggregation Protocol)
+ Definition
> PAgP is a Cisco proprietary protocol used to negotiate EtherChannel links between Cisco devices.

> Modes
+ Desirable → Actively negotiates
+ Auto → Passive, waits for PAgP

> Configuration Commands
```py
Switch(config)#interface range gig0/3-4
Switch(config-if-range)#switchport mode trunk
Switch(config-if-range)#channel-group 2 mode desirable
```
> Verification
```py
Switch#show etherchannel summary
Switch#show pagp neighbor
```
---
### 3. Static EtherChannel (Force Mode)
+ Definition
> Static EtherChannel does not use any negotiation protocol. Links are forced into a channel.
+ ⚠️ Risky if configuration mismatches.

> Configuration Commands
```py
Switch(config)#interface range gig0/5-6
Switch(config-if-range)#switchport mode trunk
Switch(config-if-range)#channel-group 3 mode on
```
> Verification
```py
Switch#show etherchannel summary
```
---
### 4. Load-Balancing Methods
+ Definition
> Load balancing decides how traffic is distributed across the physical links in an EtherChannel.

> Common Methods
+ src-mac
+ dst-mac
+ src-ip
+ dst-ip
+ src-dst-ip
+ src-dst-port

> Configuration Command
```py
Switch(config)#port-channel load-balance src-dst-ip
```
> Verification
```py
Switch#show etherchannel load-balance
```

### Important Rules (Must Remember)
+ All ports must have:
  + Same speed
  + Same duplex
  + Same VLAN configuration
+ Trunk/access mode must match
+ EtherChannel is seen as one logical interface (Port-Channel)

### Quick Comparison
```py
| Feature     | LACP  | PAgP     | Static            |
| ----------- | ----- | -------- | ----------------- |
| Standard    | IEEE  | Cisco    | None              |
| Negotiation | Yes   | Yes      | No                |
| Safe        | High  | Medium   | Low               |
| Recommended | ✅ Yes | ❌ Legacy | ❌ Not recommended |


```