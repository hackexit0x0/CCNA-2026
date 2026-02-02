# Alcatel OmniSwitch – Complete Command Reference


### 🔹 Basic Commands
```PY
help            # Shows help information
?               # Displays available commands
show            # Displays running information
exit            # Exit current mode
logout          # Logout from switch
```

### System Information
```PY
show system             # Overall system details
show system status      # System health and status
show system cpu         # CPU utilization
show system memory      # Memory usage
show system uptime      # Switch running time
show chassis            # Hardware chassis details
show hardware-info      # Hardware and module info
```

### 🔹 Configuration Mode
```PY
configure terminal      # Enter global configuration mode
write memory            # Save configuration to memory
copy running certified  # Save running config as certified config
```

### 🔹 Interface / Port Commands
```PY
show interfaces         # Show all interfaces
show interfaces status  # Port up/down status
show interfaces counters # Port traffic statistics

interfaces ethernet 1/1 # Select Ethernet port 1/1
no shutdown             # Enable the port
shutdown                # Disable the port
speed 1000              # Set speed to 1 Gbps
duplex full             # Set full duplex mode
```

### 🔹 VLAN Commands
```PY
vlan 10                 # Create VLAN 10
vlan 20                 # Create VLAN 20
vlan 10 name STAFF      # Name VLAN 10 as STAFF

interfaces ethernet 1/1
vlan participation include 10   # Assign port to VLAN 10 (access mode)

show vlan               # Show all VLANs
show vlan 10            # Show VLAN 10 details
no vlan 10              # Delete VLAN 10
```

### 🔹 Trunk / Tagged Port
```PY
interfaces ethernet 1/24
vlan participation include 10,20,30     # Allow VLANs on port
vlan participation tagging 10,20,30     # Tag VLAN traffic (trunk port)
```

### 🔹 IP & Management
```PY
ip interface vlan 1 address 192.168.1.10 mask 255.255.255.0
# Assign management IP to VLAN 1

ip default-gateway 192.168.1.1   # Set default gateway
show ip interface                # Show IP interface details
```

### 🔹 Layer 3 Routing
```py
ip routing               # Enable Layer-3 routing

ip interface vlan 10
address 10.10.10.1 mask 255.255.255.0
# Create SVI for VLAN 10

show ip routes           # Show routing table

ip route 0.0.0.0/0 gateway 192.168.1.1
# Default route to internet/router
```

### 🔹 DHCP Configuration
```py
ip dhcp pool VLAN10
network 10.10.10.0 255.255.255.0   # DHCP subnet
default-router 10.10.10.1          # Gateway for clients
dns-server 8.8.8.8                 # DNS server

ip helper-address 192.168.1.5
# Forward DHCP requests to external DHCP server
```

### 🔹 Spanning Tree Protocol (STP)
```py
show spantree          # Show STP status
spantree enable        # Enable spanning tree

interfaces ethernet 1/1
spantree portfast      # Enable PortFast (end devices only)
```
### 🔹 MAC Address Table
```py
show mac-address-table             # Show MAC table
show mac-address-table vlan 10     # MACs in VLAN 10
clear mac-address-table            # Clear MAC address table
```

### 🔹 SNMP
```py
snmp community public ro   # Read-only SNMP community
snmp community private rw  # Read-write SNMP community
show snmp                  # Show SNMP configuration
```

### 🔹 Logs & Monitoring
```py
show log        # Show system logs
show event      # Show system events
```

### 🔹 Backup & Restore
```py
copy running-config tftp 192.168.1.100 switch.cfg
# Backup configuration to TFTP server

copy tftp running-config 192.168.1.100 switch.cfg
# Restore configuration from TFTP
```

### 🔹 Reboot / Reset
```py
reload          # Reboot the switch
reload factory  # Factory reset (ERASES all config)

```

<a href="https://github.com/BryanGoble/Alcatel-Commands-Cheatsheet">Alcatel-Commands-Cheatsheet</a>