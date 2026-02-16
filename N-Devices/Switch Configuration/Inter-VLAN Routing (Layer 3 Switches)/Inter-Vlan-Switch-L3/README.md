#### ✅ METHOD 1: Inter-VLAN Routing Using **Layer 3 Switch**


#### 🔹 Step 1: Create VLANs

```py
Switch> enable
Switch# configure terminal

Switch(config)# vlan 10
Switch(config)# vlan 20
Switch(config)# vlan 30
```
#### 🔹 Step 2: Create VLAN Interfaces (SVIs)
```py
# Create SVI for VLAN 10
Switch(config)# interface vlan 10
Switch(config-if)# no shutdown
Switch(config-if)# exit

# Create SVI for VLAN 20
Switch(config)# interface vlan 20
Switch(config-if)# no shutdown
Switch(config-if)# exit

# Create SVI for VLAN 30
Switch(config)# interface vlan 30
Switch(config-if)# no shutdown
Switch(config-if)# exit
```
> 📌 SVI = Virtual interface acting as Default Gateway

#### 🔹 Step 3: Assign IP Addresses to SVIs (Option : IF have DHCP Server)
```py
### If have dhcp server then add this commands.. 
# VLAN 10 Gateway
Switch(config)# interface vlan 10
Switch(config-if)# ip address 192.168.10.1 255.255.255.0
Switch(config-if)# ip helper-address 10.0.0.100  // Forwards DHCP to server at 10.0.0.100 (Optional)
Switch(config-if)# exit


# VLAN 10 Gateway
Switch(config)# interface vlan 10
Switch(config-if)# ip address 192.168.10.1 255.255.255.0
Switch(config-if)# exit

# VLAN 20 Gateway
Switch(config)# interface vlan 20
Switch(config-if)# ip address 192.168.20.1 255.255.255.0
Switch(config-if)# exit

# VLAN 30 Gateway
Switch(config)# interface vlan 30
Switch(config-if)# ip address 192.168.30.1 255.255.255.0
Switch(config-if)# exit
```
#### 🔹 Step 4: Enable IP Routing (VERY IMPORTANT)
```py
# Enable Layer 3 routing
Switch(config)# ip routing
```
> ⚠️ Without this command, Inter-VLAN routing will NOT work

#### 🔹 Step 5: Assign Access Ports to VLANs
```py
Switch(config)# interface range fa0/1 - 4
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 10
Switch(config-if-range)# exit

Switch(config)# interface range fa0/5 - 8
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit

Switch(config)# interface range fa0/9 - 12
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 30
Switch(config-if-range)# exit
```

#### 🔍 Verification (L3 Switch)
```py
Switch# show ip interface brief
Switch# show vlan brief
Switch# show ip route
```

#### 🆚 Layer 3 Switch vs Router-on-a-Stick
| Feature          | L3 Switch      | Router        |
| ---------------- | -------------- | ------------- |
| Routing Speed    | Very Fast      | Slower        |
| Method           | SVI            | Sub-interface |
| Bottleneck       | ❌ No           | ✅ Yes         |
| Best For         | Enterprise LAN | Small Network |
| Hardware Routing | Yes            | No            |

## ✅ Important Exam Notes
- VLAN must exist before creating SVI
- ip routing is mandatory on L3 switch
- PCs use SVI / Router IP as Default Gateway
- Trunk required for router-based routing