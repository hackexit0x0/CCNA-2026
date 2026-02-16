# 🧩 Network Configuration Overview (RIP + NAT)

This lab demonstrates a multi-router network using **RIPv2** for dynamic routing and **Static NAT** to allow external access to an internal web server.

---

## 🗺 Network Topology

### Devices and IP Addresses

| Device      | Interface | IP Address       | Description |
|-------------|-----------|-----------------|-------------|
| Web Server  | NIC       | 192.168.10.2    | Connected to Router5 |
| User PC     | NIC       | 192.168.30.2    | Connected to Router7 |
| Router5     | LAN       | 192.168.10.1    | Web Server Gateway |
|             | WAN       | 10.0.0.1        | Link to Router6 |
| Router6     | G0/0      | 10.0.0.2        | Core Router |
|             | G0/1      | 20.0.0.1        | Core Router |
| Router7     | WAN       | 20.0.0.2        | Link from Router6 |
|             | LAN       | 192.168.30.1    | User PC Gateway |

---

<img src="image.png">

---

## 🛠 Step-by-Step Configuration

### 1️⃣ Assign Static IP Addresses

> **Web Server**
```PY
IP Address: 192.168.10.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.10.1

public IP : 10.0.0.1
Domain Name : hsv.io
```
> **User PC**
```PY
IP Address: 192.168.30.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.30.1

```
---

### 2️⃣ Router Interface Configuration

**Router5**
```PY
conf t
interface Gig0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown
interface Gig0/1
 ip address 10.0.0.1 255.255.255.0
 no shutdown
exit
```
> Router6
```PY
bash
conf t
interface Gig0/0
 ip address 10.0.0.2 255.255.255.0
 no shutdown
interface Gig0/1
 ip address 20.0.0.1 255.255.255.0
 no shutdown
exit
```
> Router7
```PY
conf t
interface Gig0/0
 ip address 20.0.0.2 255.255.255.0
 no shutdown
interface Gig0/1
 ip address 192.168.30.1 255.255.255.0
 no shutdown
exit
```
### Configure RIP Routing (RIPv2)
> Apply on all routers:
```PY
conf t
router rip
 version 2
 no auto-summary
 network 192.168.10.0
 network 192.168.30.0
 network 10.0.0.0
 network 20.0.0.0
exit
```
### 4️⃣ Configure Static NAT (Router5)
> Define NAT Inside and Outside Interfaces:
```PY
conf t
interface Gig0/0
 ip nat inside
interface Gig0/1
 ip nat outside
exit
```
> Static NAT Mapping:
```PY
ip nat inside source static 192.168.10.2 10.0.0.10
```
> Block Direct Access to Internal IP\
> Use an Access Control List (ACL) to deny traffic to 192.168.10.2 from outside:
```py
access-list 100 deny ip any host 192.168.10.2
access-list 100 permit ip any any
```
> This maps the internal Web Server (192.168.10.2) to the public IP 10.0.0.10.

### 5️⃣ Configure Default Routes
> Router5
```PY
ip route 0.0.0.0 0.0.0.0 10.0.0.2
```
> Router7
```PY
ip route 0.0.0.0 0.0.0.0 20.0.0.1
```