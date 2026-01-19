### NAT Configuration (Cisco IOS)

> This document provides **notes and commands** for configuring  
> **Network Address Translation (NAT)** on Cisco routers.

---

## 1. NAT Overview

> **Network Address Translation (NAT)** allows private IP addresses to communicate  
> with public networks by translating them into public IP addresses.

### Types of NAT
- **Static NAT** – One-to-One mapping  
- **Dynamic NAT** – Many-to-Many mapping using a pool  
- **PAT (NAT Overload)** – Many-to-One mapping using port numbers  


```py
Static
  |------> Static
  |------> PAT

Dynamic
  |------> Dynamic
  |------> PAT
```
## Inside and Outside Interface Configuration (Requared)

### Description
- Interfaces must be identified as inside or outside for NAT to function

### Configuration Commands
```py
Router(config)# interface GigabitEthernet0/0
# interface     → Enters interface configuration mode
# GigabitEthernet0/0 → LAN interface

Router(config-if)# ip nat inside
# ip nat inside → Marks this interface as INSIDE (private)

Router(config-if)# exit
# exit          → Leaves interface mode
```
```py
Router(config)# interface GigabitEthernet0/1
# interface     → Enters interface configuration mode
# GigabitEthernet0/1 → WAN interface

Router(config-if)# ip nat outside
# ip nat outside → Marks this interface as OUTSIDE (public)

Router(config-if)# exit
# exit           → Leaves interface mode
```


## 1. Static NAT

### Description
- Maps **one private IP** to **one public IP**
- Permanent mapping
- Commonly used for internal servers

### Configuration Command
```py
Router(config)# ip nat inside source static 192.168.1.10 203.0.113.10

ip nat inside source static (private IP) (public IP ISP)

# ip            → Global IP configuration command
# nat           → Enables Network Address Translation
# inside        → Refers to the internal (private) network
# source        → Translates the source IP address
# static        → Creates a permanent one-to-one mapping
# 192.168.1.10  → Inside local address (private IP)
# 203.0.113.10  → Inside global address (public IP)

```
---

## 3. Dynamic NAT

### Description
- Maps private IP addresses to a pool of public IPs
- Temporary allocation
- Public IP is released after use

### Configuration Commands
>  ACL (Select which IPs can be translated)
```py
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255

# access-list   → Creates an access control list
# 1             → ACL number (standard ACL)
# permit        → Allows the traffic
# 192.168.1.0   → Network address to be translated
# 0.0.0.255     → Wildcard mask (matches entire /24 network)
```
> NAT Pool (Public IP range)
```py
Router(config)# ip nat pool NATPOOL 203.0.113.10 203.0.113.20 netmask 255.255.255.0

ip nat pool NATPOOL (public ip ISP starting) (public ip ISP Ending) netmask 255.255.255.0

# ip            → IP configuration
# nat           → Network Address Translation
# pool          → Defines a pool of public IPs
# NATPOOL       → Name of the NAT pool
# 203.0.113.10  → Starting public IP address
# 203.0.113.20  → Ending public IP address
# netmask       → Subnet mask for the public network
# 255.255.255.0 → Subnet mask
```
> Bind ACL to NAT Pool
```py
Router(config)# ip nat inside source list 1 pool NATPOOL
# ip            → IP configuration
# nat           → NAT feature
# inside        → Inside (private) network
# source        → Translate source IP addresses
# list 1        → Uses ACL 1 to select inside IPs
# pool NATPOOL  → Uses the public IPs from NATPOOL
```
---

## 4. PAT (NAT Overload)

### Description
- Multiple private IPs share one public IP
- Uses port numbers to track sessions
- Most commonly used NAT type

### Configuration Command (Using Interface IP)
```py
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255

# access-list   → Selects internal IPs
# 1             → Standard ACL number
# permit        → Allows translation
# 192.168.1.0   → Private network
# 0.0.0.255     → Wildcard mask


Router(config)# ip nat inside source list 1 interface GigabitEthernet0/1 overload
# ip            → IP configuration
# nat           → NAT feature
# inside        → Inside network
# source        → Translates source IPs
# list 1        → Uses ACL 1
# interface     → Uses interface IP instead of pool
# GigabitEthernet0/1 → Outside (public) interface
# overload      → Enables PAT (multiple IPs share one public IP)
```
---



## 6. Verification Commands
```py
Router# show ip nat translations
# show          → Displays information
# ip nat        → NAT-related information
# translations  → Shows active NAT mappings
```
```py
Router# show ip nat statistics
# statistics    → Displays NAT usage details
#               → Shows hits, misses, and translation counts
```
---

### Clear NAT Table
```py
Router# clear ip nat translation *
# clear         → Removes entries
# ip nat        → NAT table
# translation   → NAT mappings
# *             → Clears ALL translations
```

If you want, I can:
- Make it **CCNA-exam optimized**
- Add **network diagrams**
- Convert it to **PDF**
- Package it as a **GitHub-ready repo**


