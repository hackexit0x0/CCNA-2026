### Vlan Configuration

### 🔹 1. Create VLANs
---
```py
Switch> enable
Switch# configure terminal

Switch(config)# vlan 10
Switch(config)# vlan 20
Switch(config)# vlan 30
```
---
### 🔹 2. Name VLANs
----
```py
Switch(config)# vlan 10
Switch(config-vlan)# name SALES
Switch(config-vlan)# exit

Switch(config)# vlan 20
Switch(config-vlan)# name HR
Switch(config-vlan)# exit

Switch(config)# vlan 30
Switch(config-vlan)# name IT
Switch(config-vlan)# exit
```
----

### 🔹 3. Assign Ports to VLANs (Access Mode)
---
> Assign FastEthernet0/1–0/4 to VLAN 10
```py
Switch(config)# interface range fa0/1 - 4
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 10
Switch(config-if-range)# exit
```
>  Assign FastEthernet0/5–0/8 to VLAN 20
```py
Switch(config)# interface range fa0/5 - 8
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit
```
> Assign FastEthernet0/9–0/12 to VLAN 30
```py
Switch(config)# interface range fa0/9 - 12
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 30
Switch(config-if-range)# exit
```
---

### 🔹 4. Verify VLAN Configuration
```py
### Show all VLANs
Switch# show vlan brief

### Show VLAN details
Switch# show vlan id 10

### Check port VLAN assignment
Switch# show interfaces fa0/1 switchport
```
### 🔹 5. Delete VLANs
```py
### Delete Single VLAN
Switch(config)# no vlan 20

### Delete Multiple VLANs
Switch(config)# no vlan 10
Switch(config)# no vlan 30

### Delete VLAN Database (Older Switches)
Switch# delete flash:vlan.dat
Switch# reload
```