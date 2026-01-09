### ============ On L2 Switch (Access Switch) ============ 

```py
enable
configure terminal

vlan 10
name VLAN10
exit

vlan 20
name VLAN20
exit

vlan 30
name VLAN30
exit
```
2️⃣ Assign Access Ports

```py

interface range fa0/1 - 5
switchport mode access
switchport access vlan 10
exit

interface range fa0/6 - 10
switchport mode access
switchport access vlan 20
exit

interface range fa0/11 - 15
switchport mode access
switchport access vlan 30
exit
```
3️⃣ Trunk Port (L2 → L3)
```py
interface fa0/24
switchport mode trunk
no shutdown
exit
```
# ------- L3 Swicth --------
> 🔹 On L3 Switch (Multilayer Switch)
> 1️⃣ Create VLANs
```py
enable
configure terminal

vlan 10
name VLAN10
exit

vlan 20
name VLAN20
exit

vlan 30
name VLAN30
exit
```
2️⃣ Enable Routing
```py
ip routing
```

3️⃣ Create SVI (Gateway Interfaces)
```py
interface vlan 10
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

interface vlan 20
ip address 192.168.20.1 255.255.255.0
no shutdown
exit

interface vlan 30
ip address 192.168.30.1 255.255.255.0
no shutdown
exit
```

4️⃣ Trunk Port (L3 → L2)

> Example Fa0/1 connects to L2:

```py
interface fa0/1
switchport mode trunk
no shutdown
exit
```

> 🔍 Verify
On both switches:
```py
show vlan brief
show interfaces trunk
```

> On L3 switch:
```py
show ip interface brief
```

