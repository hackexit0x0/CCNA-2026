### Default Routes LAB
---
<img src="image.png">


### 🔹 Network Summary (From Your Diagram)
> Router0 (Left)
- LAN: 192.168.10.0/24
- WAN to Router1: 10.0.0.0/30

> Router1 (Middle)
- LAN: 192.168.20.0/24
- WAN to Router0: 10.0.0.0/30
- WAN to Router2: 20.0.0.0/30

> Router2 (Right)
- LAN: 192.168.30.0/24
- WAN to Router1: 20.0.0.0/30
---

```py
### R1
router rip 
network 10.0.0.0
network 192.168.10.0

### R2
router rip 
network 10.0.0.0
network 20.0.0.0
network 192.168.20.0

### R3
router rip 
network 20.0.0.0
network 192.168.30.0

## show only rip routing
show ip route rip
show ip protocols



## Show routing table
show ip route
```