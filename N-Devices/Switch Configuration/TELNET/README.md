#### Enable Telnet on Cisco Switch

What is Telnet?
> **Telnet** is a remote management protocol used to access a **switch CLI** over a network.

> ⚠️ **Note:** Telnet sends data in **plain text** (not secure).  
> For real networks, **SSH is recommended**, but Telnet is still important for **CCNA labs & basics**.

---

#### Network Example
- **Switch Management IP:** 192.168.1.2  
- **VLAN:** 1  
- **Client Network:** 192.168.1.0/24  
- **Gateway (Router):** 192.168.1.1  

---

#### Configure Management IP on Switch (SVI)
```py
Switch> enable
Switch# configure terminal

Switch(config)# username admin password admin123

Switch(config)# interface vlan 1
Switch(config-if)# ip address 192.168.1.2 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

Switch(config)# ip default-gateway 192.168.1.1
```
SET ENABLE PASSWORD

```py
Switch(config)# enable password cisco
```
> Configure VTY Lines for Telnet
```py
Switch(config)# line vty 0 4
Switch(config-line)# password telnet123
Switch(config-line)# login
Switch(config-line)# transport input telnet
Switch(config-line)# exit
```

> Enable Telnet with Local Authentication
```py
Switch(config)# line vty 0 4
Switch(config-line)# login local
Switch(config-line)# transport input telnet
Switch(config-line)# exit
```
> Save Configuration
```py
Switch# write memory
```
> Verify
```py
Switch# show running-config | section vty
```

> Client Side
telnet 192.168.1.2



#### Interview Questions
Q1. Telnet Port →` TCP 23`

Q2. Secure Alternative → `SSH`

Q3. Management IP → `VLAN Interface (SVI)`


> 🔁 Next message (important)

Send **only this**: