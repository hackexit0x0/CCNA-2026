Here is the CLEAR + REAL-LAB working configuration for:

🔹 L3 Switch ↔ L2 Switch = TRUNK
🔹 L2 Switch ↔ PC = ACCESS

(Alcatel OmniSwitch syntax)

🧠 TOPOLOGY
[L3 Switch] =====(TRUNK)===== [L2 Switch] ----(ACCESS)---- PC


Example VLANs:

VLAN 10 → Users

VLAN 20 → Users

L3 switch does routing

🔷 L3 SWITCH CONFIG (TRUNK PORT)
1️⃣ Create VLANs
vlan 10
vlan 10 enable

vlan 20
vlan 20 enable

2️⃣ Create VLAN Interfaces (Gateway)
ip interface vlan 10 address 10.10.10.1 mask 255.255.255.0
ip interface vlan 20 address 10.10.20.1 mask 255.255.255.0

3️⃣ Configure TRUNK Port (to L2)

Assume uplink port = 1/1/48

vlan 10 members port 1/1/48 tagged
vlan 20 members port 1/1/48 tagged


✔ L3 side DONE

🔷 L2 SWITCH CONFIG
1️⃣ Create VLANs
vlan 10
vlan 10 enable

vlan 20
vlan 20 enable

2️⃣ TRUNK PORT (to L3 Switch)

Assume uplink port = 1/1/48

vlan 10 members port 1/1/48 tagged
vlan 20 members port 1/1/48 tagged


✅ This is L3 ↔ L2 TRUNK

3️⃣ ACCESS PORT (L2 to PC)
PC on VLAN 10 (Port 1/1/1)
vlan 10 members port 1/1/1 untagged

PC on VLAN 20 (Port 1/1/2)
vlan 20 members port 1/1/2 untagged


🖥️ PC IP Example:

IP: 10.10.10.10
Gateway: 10.10.10.1

🔍 VERIFY COMMANDS
show vlan
show vlan members
show ip interface

✅ SUMMARY TABLE
Link	Mode
L3 → L2	TRUNK (Tagged)
L2 → PC	ACCESS (Untagged)
Routing	L3 Switch