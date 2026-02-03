🔹 Add All Ports to a VLAN (Access Mode)
Example: Add ALL ports to VLAN 10
vlan 10
vlan 10 enable
vlan 10 members port 1/1-1/48 untagged


👉 1/1-1/48 = all switch ports
👉 untagged = access VLAN (for end devices)

🔹 Add Selected Range of Ports

Example: Ports 1–24 in VLAN 20

vlan 20
vlan 20 enable
vlan 20 members port 1/1-1/24 untagged

🔹 Remove Ports from VLAN
vlan 10 no members port 1/1-1/48

🔹 Verify VLAN Membership
show vlan 10
show vlan members

🔹 If You Want ALL Ports as TRUNK (Tagged)

Example: VLAN 100 tagged on all ports

vlan 100
vlan 100 enable
vlan 100 members port 1/1-1/48 tagged

🔹 Common Real-World Setup
Use Case	Mode
PC / Laptop	untagged
Switch ↔ Switch	tagged
Router / Firewall	tagged

If you want 👇
✔ Access VLAN for users
✔ Trunk uplink port config
✔ Inter-VLAN routing
✔ Cisco vs Alcatel comparison