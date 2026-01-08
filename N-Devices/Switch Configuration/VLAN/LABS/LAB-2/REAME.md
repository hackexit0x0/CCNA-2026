# --------- SWITCH 1 -------------

```py

SW-1(config)#interface range fastEthernet 0/1 - 5
SW-1(config-if-range)#switchport access vlan 10
% Access VLAN does not exist. Creating vlan 10
SW-1(config-if-range)#exit

SW-1(config)#interface range fastEthernet 0/6 - 10
SW-1(config-if-range)#switchport access vlan 20
% Access VLAN does not exist. Creating vlan 20
SW-1(config-if-range)#exit

SW-1(config)#interface range fastEthernet 0/11 - 15
SW-1(config-if-range)#switchport access vlan 30
% Access VLAN does not exist. Creating vlan 30
```


### CORE SWITCH
```py
CORE-SW-1(config)#vlan 10
CORE-SW-1(config-vlan)#name HR
CORE-SW-1(config-vlan)#exit

CORE-SW-1(config)#vlan 20
CORE-SW-1(config-vlan)#name FIN
CORE-SW-1(config-vlan)#exit

CORE-SW-1(config)#vlan 30
CORE-SW-1(config-vlan)#name Sales
CORE-SW-1(config-vlan)#exit

CORE-SW-1(config)#interface fastEthernet 0/1
CORE-SW-1(config-if)#switchport mode access 
CORE-SW-1(config-if)#switchport access vlan 10
%CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch discovered on FastEthernet0/1 (10), with SW-1 FastEthernet0/24 (1).
```