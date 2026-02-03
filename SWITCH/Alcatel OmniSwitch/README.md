🟢 ALCATEL OMNISWITCH
BASICS → ADVANCED (0 → HERO)

(With comments & explanations)

1️⃣ BASIC SYSTEM COMMANDS (START HERE)
```py
show system                 # Overall switch info
show system status          # Health, temp, fans, PSU
show system cpu             # CPU usage
show system memory          # RAM usage
show system uptime          # How long switch is running
show chassis                # Hardware details
show hardware-info          # Ports, modules info
# 💡 Used by NOC engineers for quick health checks.
```
2️⃣ BASIC CONFIG MODE
```py
configure terminal          # Enter config mode
write memory                # Save configuration
reload                      # Reboot switch

# ⚠️ Always write memory after changes.
```
3️⃣ PORT (INTERFACE) COMMANDS
```py
show interfaces             # Show all ports status
show interfaces port 1/1/1  # Specific port info

Enable / Disable Port
interfaces port 1/1/1 admin up
interfaces port 1/1/1 admin down
```

4️⃣ VLAN BASICS (CORE SKILL)
```py
# Create VLAN
vlan 10
vlan 10 enable              # Activate VLAN

# Add ACCESS Port (PC)
vlan 10 members port 1/1/1 untagged


# 👉 Untagged = Access port

# Add TRUNK Port (Switch/Router)
vlan 10 members port 1/1/48 tagged


# 👉 Tagged = Trunk port

# View VLAN Info
show vlan
show vlan members
show vlan 10
```

5️⃣ ADD ALL PORTS TO VLAN
```py
vlan 10 members port 1/1-1/48 untagged

# 💡 Used in labs / training setups.
```

6️⃣ REMOVE PORT FROM VLAN
```py
vlan 10 no members port 1/1/1
```

7️⃣ L3 SWITCHING (INTER-VLAN ROUTING)
```py
# Create VLAN Interface (Gateway)
ip interface vlan 10 address 10.10.10.1 mask 255.255.255.0

# 👉 This enables routing for VLAN.

# Enable IP Routing
ip routing

# Verify
show ip interface
show ip route

```

8️⃣ TRUNKING (REAL NETWORK)
```py
# L3 ↔ L2 Trunk
vlan 10 members port 1/1/47 tagged
vlan 20 members port 1/1/47 tagged
```

9️⃣ DHCP SERVER (ON L3 SWITCH)
```py
ip dhcp pool VLAN10
 network 10.10.10.0 mask 255.255.255.0
 default-router 10.10.10.1
 dns-server 8.8.8.8

ip dhcp enable
```

🔟 DHCP RELAY (HELPER)
```py
ip interface vlan 10 helper-address 172.16.0.10
```

1️⃣1️⃣ STATIC ROUTE
```py
ip route 0.0.0.0 0.0.0.0 172.16.0.1

# 👉 Default route to router/firewall.
```

1️⃣2️⃣ ACCESS CONTROL LIST (ACL)
```py
# Create ACL
ip access-list extended BLOCK_VLAN20
 deny ip 10.10.20.0 0.0.0.255 10.10.10.0 0.0.0.255
 permit ip any any

# Apply ACL
ip interface vlan 20 access-group BLOCK_VLAN20 in
```

1️⃣3️⃣ PORT SECURITY
```py
interfaces port 1/1/1 port-security enable
interfaces port 1/1/1 port-security maximum 1
```

1️⃣4️⃣ STP (LOOP PROTECTION)
```py
show spantree
spantree enable
```

1️⃣5️⃣ LINK AGGREGATION (LACP)
```py
linkagg 1 admin up
linkagg 1 port 1/1/45,1/1/46
```


1️⃣6️⃣ SNMP (MONITORING)
```py
snmp community public ro
snmp enable
```

1️⃣7️⃣ BACKUP CONFIG
```py
copy running-config working
copy working-config flash
```

1️⃣8️⃣ LOGGING & TROUBLESHOOTING
```py
show log swlog
show arp
show mac-address-table
ping 10.10.10.10
traceroute 8.8.8.8
```

🎯 REAL INTERVIEW QUESTIONS THIS COVERS
```py
✔ VLAN / Trunk / Access
✔ L3 Routing
✔ DHCP / ACL
✔ STP / LACP
✔ Troubleshooting
```