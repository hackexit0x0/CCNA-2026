✅ L3 SWITCH CONFIGURATION CHECKLIST (COMPLETE)
### 1️⃣ Basic L3 Switch Configuration

+ Hostname
+ Login Banner (MOTD / Legal)
+ Console password
+ VTY (SSH/Telnet) password
+ Enable secret
+ Service password encryption
+ Management VLAN (SVI)
+ IP address on SVI
+ Default gateway (for management only)
+ Enable IP routing (mandatory on L3)

2️⃣ VLAN Configuration

+ Create VLANs
+ VLAN naming
+ Assign access ports to VLANs
+ Verify VLAN database
+ Delete unused VLANs

3️⃣ Trunk Configuration

+ Trunk ports enable
+ 802.1Q encapsulation
+ Allowed VLAN list
+ Native VLAN
+ Trunk verification

4️⃣ Inter-VLAN Routing (Core L3 Feature)

+ Create VLAN interfaces (SVIs)
+ Assign IP to each VLAN
+ Enable ip routing
+ Test inter-VLAN connectivity
+ Static routing (if required)
+ Dynamic routing (OSPF / RIP / EIGRP – optional)

5️⃣ Spanning Tree Protocol (STP)

+ STP enabled
+ Root bridge selection
+ PortFast (Access ports)
+ BPDU Guard
+ BPDU Filter
+ Loop Guard
+ Root Guard

6️⃣ Port Security

+ Maximum MAC limit
+ Sticky MAC learning
+ Violation mode
 ▫ Protect
 ▫ Restrict
 ▫ Shutdown
+ Aging time configuration

7️⃣ EtherChannel / Link Aggregation

+ LACP
+ PAgP
+ Static EtherChannel
+ Load-balancing method
+ Interface consistency check

8️⃣ DHCP Features (L3 Switch Power)

+ DHCP Snooping
+ Trusted / untrusted ports
+ DHCP Option 82
+ DHCP Relay (ip helper-address)
+ Local DHCP server (if used)

9️⃣ Access Control Lists (ACL) (IMPORTANT for CEH)
ACL Types Supported on L3 Switch

+ Standard ACL
+ Extended ACL
+ VLAN ACL (VACL)
+ Router ACL (RACL – on SVI)
+ Port ACL (PACL)

ACL Application Checklist

+ Apply on SVI
+ Apply on VLAN
+ Apply on Interface
+ Direction control (IN / OUT)
+ Traffic filtering & segmentation

🔟 Security Features

+ Dynamic ARP Inspection (DAI)
+ IP Source Guard
+ 802.1X Authentication
+ Storm Control (Broadcast / Multicast / Unknown Unicast)
+ Private VLANs (Advanced)

1️⃣1️⃣ Quality of Service (QoS)

+ Traffic classification
+ DSCP / CoS marking
+ Trust boundary
+ Queue management
+ Policing
+ Shaping

1️⃣2️⃣ Switching Fundamentals

+ Access ports
+ Trunk ports
+ MAC address table
+ MAC aging time
+ Port negotiation modes
 ▫ Access
 ▫ Trunk
 ▫ Dynamic Auto
 ▫ Dynamic Desirable

1️⃣3️⃣ Monitoring & Troubleshooting

+ SPAN / RSPAN
+ SNMP (v2 / v3)
+ Syslog server
+ CDP / LLDP
+ Speed & duplex configuration
+ Interface error counters

1️⃣4️⃣ High Availability (Advanced L3)

+ StackWise
+ Virtual Switching System (VSS)
+ Redundant uplinks
+ HSRP / VRRP / GLBP
+ Gateway failover testing