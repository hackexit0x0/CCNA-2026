## 🔸 What is DHCP?
**DHCP (Dynamic Host Configuration Protocol)** automatically assigns:
- IP Address  
- Subnet Mask  
- Default Gateway  
- DNS Server  

to client devices (PCs, laptops, phones).

---

## 🔹 Network Example
- **Network:** 192.168.1.0/24  
- **Gateway:** 192.168.1.1  
- **DNS:** 8.8.8.8  

---

> Configure IP on Router Interface
```bash
Router> enable
Router# configure terminal

Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
# ✅ This IP will act as the Default Gateway

# Exclude IP Addresses (Important)
# Used for router, server, or static IPs.

Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
# DHCP will NOT assign these IPs

# Create DHCP Pool
Router(config)# ip dhcp pool LAN_POOL

# Define Network Range
Router(dhcp-config)# network 192.168.1.0 255.255.255.0

# Configure Default Gateway
Router(dhcp-config)# default-router 192.168.1.1 

# Configure DNS Server
Router(dhcp-config)# dns-server 8.8.8.8

# (Optional) Set Domain Name
Router(dhcp-config)# domain-name docxinfo.local

# Exit Configuration
Router(dhcp-config)# exit
Router(config)# exit
```
> ✅ DHCP Configuration DONE 🎉
```py
# Verify DHCP Configuration
# 🔍 Check DHCP Pool

Router# show ip dhcp pool

# 🔍 Check Assigned IPs
Router# show ip dhcp binding

#🔍 Check DHCP Configuration
Router# show running-config | section dhcp

# Client Side (PC)
#Set IP Configuration → DHCP / Automatic
```
> Test connectivity: `ping 192.168.1.1`

