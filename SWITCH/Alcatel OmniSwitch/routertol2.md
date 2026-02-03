🔷 ROUTER CONFIG (TRUNK – Sub-Interfaces)

(Cisco Router – most common in labs)

Router Interface connected to L2 Switch

Assume: GigabitEthernet0/0

conf t
interface GigabitEthernet0/0
 no shutdown

VLAN 10
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 10.10.10.1 255.255.255.0

VLAN 20
interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 10.10.20.1 255.255.255.0


✔ Router TRUNK ready
✔ Router acts as Gateway

🔷 L2 SWITCH CONFIG (Alcatel OmniSwitch)
1️⃣ Create VLANs
vlan 10
vlan 10 enable

vlan 20
vlan 20 enable

2️⃣ TRUNK PORT (L2 ↔ Router)

Assume uplink port = 1/1/48

vlan 10 members port 1/1-48 tagged
vlan 20 members port 1/1-48 tagged


📌 This makes Router ↔ L2 = TRUNK

3️⃣ ACCESS PORT (L2 ↔ PC)
PC in VLAN 10 (Port 1/1/1)
vlan 10 members port 1/1/1 untagged

PC in VLAN 20 (Port 1/1/2)
vlan 20 members port 1/1/2 untagged

🖥️ PC IP SETTINGS
PC in VLAN 10
IP Address : 10.10.10.10
Subnet     : 255.255.255.0
Gateway    : 10.10.10.1

PC in VLAN 20
IP Address : 10.10.20.10
Subnet     : 255.255.255.0
Gateway    : 10.10.20.1

🔍 VERIFY COMMANDS
Router
show ip interface brief

L2 Switch
show vlan
show vlan members

✅ FINAL SUMMARY
Link	Mode
Router ↔ L2 Switch	TRUNK (802.1Q)
L2 Switch ↔ PC	ACCESS (Untagged)
Inter-VLAN Routing