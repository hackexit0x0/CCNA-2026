## DHCP Snooping

> DHCP Snooping is a **Layer 2 security feature** that protects the network from **rogue DHCP servers**.

### Key Functions
- Filters untrusted DHCP messages  
- Allows DHCP responses only from **trusted ports**  
- Prevents attacks such as:
  - Rogue DHCP servers
  - DHCP starvation attacks

### How It Works
- Switch ports are classified as:
  - **Trusted**: Connected to legitimate DHCP servers
  - **Untrusted**: Connected to clients
- DHCP **OFFER** and **ACK** messages are blocked on untrusted ports

```py
DHCP Snooping Configuration
# Enable DHCP Snooping globally
ip dhcp snooping

# Enable DHCP Snooping on required VLANs
ip dhcp snooping vlan 10,20

# Trust the interface connected to the DHCP server
interface GigabitEthernet0/1
 ip dhcp snooping trust

# Limit DHCP packets on access ports (mitigates starvation attacks)
interface GigabitEthernet0/2
 ip dhcp snooping limit rate 10
```

### DHCP Snooping Binding Table
The switch builds a table containing:
- MAC address
- IP address
- VLAN
- Interface
- Lease time

This table is also used by other security features such as:
- Dynamic ARP Inspection (DAI)
- IP Source Guard

```py
# View DHCP Snooping binding table
show ip dhcp snooping binding
```


### Benefits
- Enhances network security
- Prevents unauthorized IP assignment
- Improves trust in DHCP operations

---

## DHCP Option 82 (Relay Agent Information Option)

DHCP Option 82 adds extra information to DHCP requests to help identify the **client’s location** in the network.

### Information Added
- **Circuit ID** (switch port, VLAN)
- **Remote ID** (switch identifier)

### How It Works
1. Client sends DHCP **DISCOVER**
2. Switch or relay agent inserts **Option 82**
3. DHCP server uses this information to:
   - Assign IP addresses based on location
   - Apply specific policies
```py
# DHCP Snooping must be enabled first
ip dhcp snooping

# Enable Option 82 insertion
ip dhcp snooping information option

# (Optional) Allow packets with Option 82 from untrusted sources
ip dhcp snooping information option allow-untrusted

# Trust uplink interface toward DHCP server
interface GigabitEthernet0/1
 ip dhcp snooping trust

```
### Use Cases
- Per-port or per-VLAN IP address assignment
- Improved IP address management
- Enhanced security and tracking

### Relationship with DHCP Snooping
- Often used together
- Option 82 is inserted only on **untrusted ports**
- Trusted ports forward packets unchanged

---

## DHCP Relay (Layer 3 Switches)

DHCP Relay allows DHCP clients and servers to communicate **across different subnets**.

### Why DHCP Relay Is Needed
- DHCP uses broadcast messages
- Routers do **not forward broadcasts** by default
- Relay converts broadcasts into unicasts

### How It Works
1. Client sends DHCP **DISCOVER** (broadcast)
2. Layer 3 switch/router:
   - Receives the broadcast
   - Forwards it as a unicast to the DHCP server
3. DHCP server replies to the relay
4. Relay forwards the response to the client
```py
# Configure DHCP Relay on a VLAN interface
interface Vlan10
 ip address 192.168.10.1 255.255.255.0
 ip helper-address 192.168.100.10


# OR configure on a routed interface
interface GigabitEthernet0/0
 ip address 192.168.20.1 255.255.255.0
 ip helper-address 192.168.100.10

```

### Common Configuration Concept
- Uses an **IP helper address**
- Configured on the VLAN or routed interface

### Benefits
- Centralized DHCP servers
- Reduced administrative overhead
- Scalable enterprise network design

---

## Summary Table

| Feature         | Purpose                         | Layer |
|-----------------|----------------------------------|-------|
| DHCP Snooping   | Prevent rogue DHCP servers       | L2    |
| DHCP Option 82  | Identify client location         | L2/L3 |
| DHCP Relay      | Enable DHCP across subnets       | L3    |
