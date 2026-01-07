## Subnetting
### ✅ 1️⃣ What is Classful Networking?
```sh
Classful networking is the old IP addressing system (before CIDR).
In classful networking, IP addresses were divided into fixed classes:

Class A → /8
Class B → /16
Class C → /24
Class D → Multicast
Class E → Research

✔ Key Features
Subnet mask is fixed, based on class
Routers do NOT send subnet mask in routing updates
All subnets in the same major network must use the same subnet mask (FLSM)
No VLSM support
Used in old routing protocols (RIPv1)

✔ Example
IP: 192.168.10.5
Classful mask = 255.255.255.0 (/24)
Because 192.x = Class C

Even if you want different subnet sizes, you must use /24 everywhere.

✔ Routing Example (Classful)
Router learns:
192.168.10.0 

It automatically assumes mask /24.
```
### ✅ 2️⃣ What is Classless Networking? (CIDR)
```
Classless networking removes the dependency on A/B/C classes.
CIDR = Classless Inter-Domain Routing

✔ Key Features
Subnet mask not fixed
Supports VLSM
You can create any prefix: /8, /9, /10… up to /30
Routers send mask information in routing updates

Modern routing protocols use it:
RIP v2
OSPF
EIGRP
BGP

✔ Example
You want:
Dept A → 100 hosts → /25
Dept B → 50 hosts → /26
Dept C → 20 hosts → /27
This is allowed in classless networking.

✔ Routing Example (Classless)
Router learns:
192.168.10.0/26
192.168.10.64/27
192.168.10.96/25

```
Each route carries prefix length.
1️⃣ FLSM Subnetting (Fixed Length Subnet Mask)
2️⃣ VLSM Subnetting (Variable Length Subnet Mask)