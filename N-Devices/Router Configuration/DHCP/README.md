### DHCP Configuration on Cisco Router

#### 🔸 What is DHCP?
> DHCP (Dynamic Host Configuration Protocol) automatically assigns:
- IP Address  
- Subnet Mask  
- Default Gateway  
- DNS Server  

> to client devices (PCs, laptops, phones).

---

> Network Example
- **Network:** 192.168.1.0/24  
- **Gateway:** 192.168.1.1  
- **DNS:** 8.8.8.8  

---

### STEP 1: CONFIGUR IP ON ROUTER INTERFACE
```py
Router> enable
Router# configure terminal

Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

# ✅ This IP will act as the Default Gateway
```

### STEP 2: Exclude IP Addresses (Important)
```py
# Used for router, server, or static IPs.

Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10

# NOET : Resrver 192.168.1.1 TO 9 Ips
# ➡️ DHCP will NOT assign these IPs

# Create DHCP Pool
Router(config)# ip dhcp pool LAN_POOL

# Define Network Range
Router(dhcp-config)# network 192.168.1.0 255.255.255.0

```
Skip to content
Chat history



You said:
howt to configur edhcp in router configure command 
ChatGPT said:
Below is a simple, CCNA-friendly step-by-step guide to configure DHCP on a Cisco Router using CLI commands 👇
(Explained in easy language, useful for labs + interviews)

🔹 DHCP Configuration on Cisco Router
🔸 What is DHCP?
DHCP (Dynamic Host Configuration Protocol) automatically gives:

IP Address

Subnet Mask

Default Gateway

DNS Server

to client devices (PCs, laptops, phones).

🔹 Network Example
Network: 192.168.1.0/24
Gateway: 192.168.1.1
DNS: 8.8.8.8
🔹 Step 1: Configure IP on Router Interface
Router> enable
Router# configure terminal

Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
✅ This IP will act as Default Gateway

🔹 Step 2: Exclude IP Addresses (Important)
Used for router, server, or static IPs.

Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
➡️ DHCP will NOT assign these IPs

🔹 Step 3: Create DHCP Pool
Router(config)# ip dhcp pool LAN_POOL
🔹 Step 4: Define Network Range
Router(dhcp-config)# network 192.168.1.0 255.255.255.0
🔹 Step 5: Configure Default Gateway
Router(dhcp-config)# default-router 192.168.1.1
🔹 Step 6: Configure DNS Server
Router(dhcp-config)# dns-server 8.8.8.8
🔹 Step 7: (Optional) Set Domain Name
Router(dhcp-config)# domain-name docxinfo.local
🔹 Step 8: Exit Configuration
Router(dhcp-config)# exit
Router(config)# exit
✅ DHCP Configuration DONE 🎉
🔹 Verify DHCP Configuration
🔍 Check DHCP Pool
Router# show ip dhcp pool
🔍 Check Assigned IPs
Router# show ip dhcp binding
🔍 Check DHCP Configuration
Router# show running-config | section dhcp
🔹 Client Side (PC)
Set IP Configuration → DHCP / Automatic
Then test:

ping 192.168.1.1
🔹 Common Interview Questions (Quick)
Why exclude IP addresses?
➝ To reserve IPs for router/servers

Can router act as DHCP server?
➝ Yes

DHCP uses which ports?
➝ UDP 67 (Server) & 68 (Client)

If you want:
✅ DHCP Relay configuration
✅ Multiple DHCP pools
✅ Packet Tracer lab diagram
✅ README.md format for GitHub

Just tell me 👍

You said:
give me command readem.md fomat 🔹 DHCP Configuration on Cisco Router
🔸 What is DHCP?

DHCP (Dynamic Host Configuration Protocol) automatically gives:

IP Address

Subnet Mask

Default Gateway

DNS Server

to client devices (PCs, laptops, phones).

🔹 Network Example
Network: 192.168.1.0/24
Gateway: 192.168.1.1
DNS: 8.8.8.8

🔹 Step 1: Configure IP on Router Interface
Router> enable
Router# configure terminal

Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit


✅ This IP will act as Default Gateway

🔹 Step 2: Exclude IP Addresses (Important)

Used for router, server, or static IPs.

Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10


➡️ DHCP will NOT assign these IPs

🔹 Step 3: Create DHCP Pool
Router(config)# ip dhcp pool LAN_POOL

🔹 Step 4: Define Network Range
Router(dhcp-config)# network 192.168.1.0 255.255.255.0

🔹 Step 5: Configure Default Gateway
Router(dhcp-config)# default-router 192.168.1.1

🔹 Step 6: Configure DNS Server
Router(dhcp-config)# dns-server 8.8.8.8

🔹 Step 7: (Optional) Set Domain Name
Router(dhcp-config)# domain-name docxinfo.local

🔹 Step 8: Exit Configuration
Router(dhcp-config)# exit
Router(config)# exit

✅ DHCP Configuration DONE 🎉
🔹 Verify DHCP Configuration
🔍 Check DHCP Pool
Router# show ip dhcp pool

🔍 Check Assigned IPs
Router# show ip dhcp binding

🔍 Check DHCP Configuration
Router# show running-config | section dhcp

🔹 Client Side (PC)

Set IP Configuration → DHCP / Automatic
Then test:

ping 192.168.1.1

🔹 Common Interview Questions (Quick)

Why exclude IP addresses?
➝ To reserve IPs for router/servers

Can router act as DHCP server?
➝ Yes

DHCP uses which ports?
➝ UDP 67 (Server) & 68 (Client)
ChatGPT said:
# 🔹 DHCP Configuration on Cisco Router

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

