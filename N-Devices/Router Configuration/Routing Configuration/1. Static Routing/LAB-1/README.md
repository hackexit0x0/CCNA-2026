#### 🛠 Static Routing Configuration

---
<img src="image.png">

---


```py

### R1
ip address 192.168.20.0 255.255.255.0 10.0.0.2
ip address 192.168.30.0 255.255.255.0 10.0.0.2
ip address 20.0.0.0 255.0.0.0 10.0.0.2

### R2
ip address 192.168.10.0 255.255.255.0 10.0.0.1
ip address 192.168.30.0 255.255.255.0 20.0.0.2

### R3
ip address 192.168.10.0 255.255.255.0 20.0.0.1
ip address 192.168.20.0 255.255.255.0 20.0.0.1
ip address 10.0.0.0 255.0.0.0 20.0.0.1

## show only static routing
show ip route static


## Show routing table
show ip route

```
