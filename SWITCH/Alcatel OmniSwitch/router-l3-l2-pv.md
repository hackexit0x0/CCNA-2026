’ll give you clean, step-by-step WORKING commands for:

🔹 Router → L3 Switch → L2 Switch = TRUNK
🔹 L2 Switch → PC = ACCESS

(Using Cisco Router + Alcatel OmniSwitch L3/L2)

🧠 TOPOLOGY
[Router]
   |
 (TRUNK)
   |
[L3 Switch]
   |
 (TRUNK)
   |
[L2 Switch] ---- ACCESS ---- PC


Example VLANs:

VLAN 10 → Users

VLAN 20 → Users

Routing done on L3 Switch

🔷 ROUTER CONFIG (TRUNK to L3 SWITCH)

Assume router interface = G0/0

conf t
interface GigabitEthernet0/0
 no shutdown

Router does NOT route VLANs here (L3 switch does)

(Just passing VLANs)

✔ Router ready

🔷 L3 SWITCH CONFIG (Alcatel OmniSwitch)
1️⃣ Create VLANs
vlan 10
vlan 10 enable

vlan 20
vlan 20 enable

2️⃣ Create VLAN Interfaces (Gateway on L3 Switch)
ip interface vlan 10 address 10.10.10.1 mask 255.255.255.0
ip interface vlan 20 address 10.10.20.1 mask 255.255.255.0

3️⃣ TRUNK PORT (L3 → Router)

Assume port = 1/1/48

vlan 10 members port 1/1/48 tagged
vlan 20 members port 1/1/48 tagged

4️⃣ TRUNK PORT (L3 → L2 Switch)

Assume port = 1/1/47

vlan 10 members port 1/1/47 tagged
vlan 20 members port 1/1/47 tagged


✔ L3 switch done (Routing + Trunks)

🔷 L2 SWITCH CONFIG (Alcatel OmniSwitch)
1️⃣ Create VLANs
vlan 10
vlan 10 enable

vlan 20
vlan 20 enable

2️⃣ TRUNK PORT (L2 → L3 Switch)

Assume uplink = 1/1/48

vlan 10 members port 1/1/48 tagged
vlan 20 members port 1/1/48 tagged

3️⃣ ACCESS PORT (L2 → PC)
PC in VLAN 10
vlan 10 members port 1/1/1 untagged

PC in VLAN 20
vlan 20 members port 1/1/2 untagged

🖥️ PC IP CONFIG
VLAN 10 PC
IP      : 10.10.10.10
Mask    : 255.255.255.0
Gateway : 10.10.10.1

VLAN 20 PC
IP      : 10.10.20.10
Mask    : 255.255.255.0
Gateway : 10.10.20.1

🔍 VERIFY COMMANDS
L3 / L2 Switch
show vlan
show vlan members
show ip interface