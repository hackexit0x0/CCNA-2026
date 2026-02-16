### 🔗 Trunk Configuration (Cisco Switch)

### 📌 What is Trunking?
> A **trunk port** is a switch port that carries **multiple VLANs** over a **single physical link**.

> Trunking uses **IEEE 802.1Q (dot1q)** encapsulation to **tag VLAN information** inside Ethernet frames.

---

### 🧠 Why Trunking is Needed
- Reduces number of physical cables
- Allows VLANs to communicate across switches
- Required for Inter-VLAN Routing
- Used in enterprise & campus networks

---

### 🧩 Role of Network Devices in Trunking

### 🔹 L2 Switch (Layer 2)
- Creates VLANs
- Assigns access ports to VLANs
- Uses trunk ports to forward VLAN traffic
- ❌ Cannot route between VLANs

> NOTE : PCs in VLAN 10 and VLAN 20 on same switch

---

### 🔹 L3 Switch (Layer 3)
- Works as **Switch + Router**
- Routes VLANs using **SVI (interface vlan X)**
- Uses trunk between L2 and L3 switches

> NOTE : Core switch routing VLANs in office network

---

### 🔹 Router
- Performs **Inter-VLAN Routing**
- Uses **Router-on-a-Stick**
- Connected to switch via trunk port

> NOTE : One router handling VLAN 10, 20, 30

---

### 🔹 When to Use Trunk Ports
- Switch ↔ Switch
- Switch ↔ Router
- L2 Switch ↔ L3 Switch

---

### 🔹 Trunk Encapsulation Types
- **802.1Q** → IEEE standard (Used in CCNA)
- ISL → Cisco proprietary (Obsolete)

---

### 🔹 Configure Trunk Port (Basic)

```py
### Enter privileged mode
Switch> enable

### Enter global configuration mode
Switch# configure terminal

### Select interface
Switch(config)# interface fa0/24

### Set port to trunk mode
Switch(config-if)# switchport mode trunk

### Exit interface mode
Switch(config-if)# exit
```
### 🔹 Configure Trunk with 802.1Q (If Required)
```py
### Select interface
Switch(config)# interface fa0/24

### Set encapsulation to dot1q
Switch(config-if)# switchport trunk encapsulation dot1q

### Enable trunk mode
Switch(config-if)# switchport mode trunk

### Exit
Switch(config-if)# exit
```
> ⚠️ Some switches auto-select encapsulation.

### 🔹 Allow Specific VLANs on Trunk
```py
### Select trunk interface
Switch(config)# interface fa0/24

### Allow only VLAN 10, 20, 30
Switch(config-if)# switchport trunk allowed vlan 10,20,30

### Exit
Switch(config-if)# exit
```
### ➕ Add VLAN to Existing Trunk
```py
Switch(config-if)# switchport trunk allowed vlan add 40
```
### ❌ Remove VLAN from Trunk
```py
Switch(config-if)# switchport trunk allowed vlan remove 20
```
### 🔹 Set Native VLAN (Optional)
```py
### Select trunk interface
Switch(config)# interface fa0/24

### Set native VLAN
Switch(config-if)# switchport trunk native vlan 99

### Exit
Switch(config-if)# exit
```
### 📌 Native VLAN traffic is UNTAGGED
> Default native VLAN = VLAN 1\
> Verify Trunk Configuration
```py
### Show all trunk ports
Switch# show interfaces trunk

### Show detailed interface trunk info
Switch# show interfaces fa0/24 switchport

### Show VLAN information
Switch# show vlan brief
```
### 🔹 Disable Trunk (Convert to Access Port)
```py
### Select interface
Switch(config)# interface fa0/24

### Change to access mode
Switch(config-if)# switchport mode access

### Assign VLAN
Switch(config-if)# switchport access vlan 10

### Exit
Switch(config-if)# exit
```
✅ CCNA Exam Quick Summary
| Feature      | Access Port | Trunk Port      |
| ------------ | ----------- | --------------- |
| VLANs        | One         | Multiple        |
| VLAN Tagging | No          | Yes (802.1Q)    |
| Used For     | End devices | Switch / Router |
| Native VLAN  | ❌           | ✅               |
