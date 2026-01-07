### 🔐 Enable SSH on Cisco Switch
> This guide explains how to enable SSH access on a Cisco Switch (Layer 2 / Layer 3) step by step, in the same format as the router guide.

```py
# Enter Privileged & Global Configuration Mode
Switch> enable
Switch# configure terminal

# Set Hostname (Required for SSH)
Switch(config)# hostname S1

# Set Domain Name (Required for SSH)
S1(config)# ip domain-name lab.local

# Create Local User
S1(config)# username admin privilege 15 secret admin@123

# Generate RSA Key
S1(config)# crypto key generate rsa


# When prompted:
# How many bits in the modulus [512]: 2048

# Enable SSH Version 2
S1(config)# ip ssh version 2

# Configure Management IP (VERY IMPORTANT for Switch)
# SSH needs an IP address on the switch (SVI)

S1(config)# interface vlan 1
S1(config-if)# ip address 10.0.0.2 255.255.255.0
S1(config-if)# no shutdown
S1(config-if)# exit

# Set Default Gateway (If accessing from another network)
S1(config)# ip default-gateway 10.0.0.1

# Configure VTY Lines for SSH Only
S1(config)# line vty 0 4
S1(config-line)# login local
S1(config-line)# transport input ssh
S1(config-line)# exit

# (Optional but Recommended) Set Enable Secret
S1(config)# enable secret enable@123

# Save Configuration
S1# write memory

```

+ ✅ Verify SSH
```py
S1# show ip ssh
S1# show crypto key mypubkey rsa
S1# show ip interface brief
```

+ 🔐 SSH Login from PC
```py
ssh admin@10.0.0.2
or
ssh -l admin 10.0.0.2
```

#### ⚠️ Common Issues
> ❌ No VLAN IP address → SSH won’t work\
> ❌ RSA key not generated → SSH fails\
> ❌ VTY set to Telnet → SSH blocked\
> ❌ VLAN interface shutdown → No connectivity