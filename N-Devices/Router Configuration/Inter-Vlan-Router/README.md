### 🔀 VLAN & Inter-VLAN Routing (Router-on-a-Stick)
#### 🔹 What is VLAN?
> VLAN (Virtual LAN) logically divides a switch into multiple broadcast domains.

> Why VLAN?
- Better security 🔐
- Reduced broadcast traffic
- Easy management

#### 🔹 What is Inter-VLAN Routing?
> VLANs cannot communicate directly.
Inter-VLAN Routing allows communication between different VLANs using a Layer-3 device.

#### 🔹 What is Router-on-a-Stick (ROAS)?
- Router-on-a-Stick is a method where:
- One physical router interface
- Uses multiple sub-interfaces
- Each sub-interface handles one VLAN
- Uses 802.1Q (Dot1Q) trunking

#### 📌 Used when Layer-3 switch is NOT available

<img src="https://www.ciscopress.com/content/images/chap4_9780136729358/elementLinks/04fig01.jpg">

🧱 Network Topology Example
```py
PC1 (VLAN 10) ----|
PC2 (VLAN 20) ----| L2 SWITCH ===== TRUNK ===== ROUTER
PC3 (VLAN 30) ----|
```

| VLAN | Network         | Gateway      |
| ---- | --------------- | ------------ |
| 10   | 192.168.10.0/24 | 192.168.10.1 |
| 20   | 192.168.20.0/24 | 192.168.20.1 |
| 30   | 192.168.30.0/24 | 192.168.30.1 |

#### 🟢 STEP-1: VLAN Creation (Switch)
```py
Switch> enable
Switch# configure terminal

! Create VLAN 10
Switch(config)# vlan 10
Switch(config-vlan)# name SALES
Switch(config-vlan)# exit

! Create VLAN 20
Switch(config)# vlan 20
Switch(config-vlan)# name HR
Switch(config-vlan)# exit

! Create VLAN 30
Switch(config)# vlan 30
Switch(config-vlan)# name IT
Switch(config-vlan)# exit
```

#### 🟢 STEP-2: Assign Access Ports to VLANs
```py
! Port for VLAN 10
Switch(config)# interface fastEthernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

! Port for VLAN 20
Switch(config)# interface fastEthernet0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# exit

! Port for VLAN 30
Switch(config)# interface fastEthernet0/3
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 30
Switch(config-if)# exit
```

#### 🟢 STEP-3: Configure Trunk Port (Switch → Router)
```py
! Interface connected to router
Switch(config)# interface fastEthernet0/24
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk encapsulation dot1q
Switch(config-if)# no shutdown
Switch(config-if)# exit
```
> 📌 Trunk carries multiple VLANs using 802.1Q

#### 🟢 STEP-4: Router Sub-Interfaces (Router-on-a-Stick)
```py
Router> enable
Router# configure terminal

! Enable physical interface
Router(config)# interface gigabitEthernet0/0
Router(config-if)# no shutdown
Router(config-if)# exit

! VLAN 10 Sub-Interface
Router(config)# interface gigabitEthernet0/0.10
Router(config-if)# encapsulation dot1Q 10   ! VLAN ID 10
Router(config-if)# ip address 192.168.10.1 255.255.255.0
Router(config-if)# exit

! VLAN 20 Sub-Interface
Router(config)# interface gigabitEthernet0/0.20
Router(config-if)# encapsulation dot1Q 20
Router(config-if)# ip address 192.168.20.1 255.255.255.0
Router(config-if)# exit

! VLAN 30 Sub-Interface
Router(config)# interface gigabitEthernet0/0.30
Router(config-if)# encapsulation dot1Q 30
Router(config-if)# ip address 192.168.30.1 255.255.255.0
Router(config-if)# exit
```
#### 🔹 What is Dot1Q Encapsulation?
> IEEE 802.1Q adds a VLAN tag to Ethernet frames.\
`encapsulation dot1Q <VLAN-ID>`

- ✔ Identifies which VLAN traffic belongs to
- ✔ Required for trunking
- ✔ Used in ROAS

#### 🧪 Verification Commands
```py
### Switch
show vlan brief
show interfaces trunk

### Router
show ip interface brief
show running-config
```
#### ✅ Advantages of Router-on-a-Stick
- ✔ Cost-effective
- ✔ Simple setup
- ✔ Works with L2 switches

#### ❌ Disadvantages
- ❌ Single link bottleneck- 
- ❌ Slower than L3 switch- 
- ❌ Not suitable for large networks

#### 📌 Summary
- VLAN separates networks
- Trunk carries multiple VLANs
- Sub-interfaces route VLAN traffic
- Dot1Q identifies VLAN IDs
- Router-on-a-Stick enables Inter-VLAN routing

