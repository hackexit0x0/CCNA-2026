


✅ CORE SWITCH (L3) – COMPLETE CONFIG
```py
enable
configure terminal

# L3 ROUTING
ip routing

# CRETAE VLAN
vlan 10
 name VLAN10
vlan 20
 name VLAN20
vlan 30
 name VLAN30
vlan 40
 name VLAN40

# VLAN FLOW DHCP,IN VLAN CONFIG
interface Vlan10
 ip address 10.1.10.1 255.255.255.0
 ip helper-address 172.16.0.10
 ip helper-address 172.16.0.11
 no shutdown
!

interface Vlan20
 ip address 10.1.20.1 255.255.255.0
 ip helper-address 172.16.0.10
 ip helper-address 172.16.0.11
 no shutdown
!

interface Vlan30
 ip address 10.1.30.1 255.255.255.0
 ip helper-address 172.16.0.10
 ip helper-address 172.16.0.11
 no shutdown
!

interface Vlan40
 ip address 10.1.40.1 255.255.255.0
 ip helper-address 172.16.0.10
 ip helper-address 172.16.0.11
 no shutdown
!

## L3 TO L2 Vlan PASss Trunking S/W1
interface GigabitEthernet1/0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40
 no shutdown

## L3 TO L2 Vlan PASss Trunking S/W1
interface GigabitEthernet1/0/2
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40
 no shutdown

## L3 TO L2 Vlan PASss Trunking S/W1
interface GigabitEthernet1/0/3
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40
 no shutdown


# L3 SWITCH ROUTING L3 >> ROUTER  
ip route 0.0.0.0 0.0.0.0 10.1.50.1

###### Routed Port (CORE → ROUTER) ######################

# LAN G/W
interface GigabitEthernet1/0/23
 no switchport
 ip address 10.1.50.2 255.255.255.0
 no shutdown


# SERVER G/W
interface GigabitEthernet3/0
 no switchport
 ip address 172.16.0.1 255.255.0.0
 no shutdown

################ L2 SWITCH COMMAND  S/W1 ########################

# ADD VLAN IN PORTS
interface range fastEthernet 0/1-5
switchport mode access 
switchport access vlan 10
exit

interface range fastEthernet 0/6-10
switchport mode access 
switchport access vlan 20
exit

interface range fastEthernet 0/11-15
switchport mode access 
switchport access vlan 30
exit

interface range fastEthernet 0/15-20
switchport mode access 
switchport access vlan 40
exit

interface gigabitEthernet 0/1
switchport mode trunk 

################ L2 SWITCH COMMAND  S/W2 ########################

# ADD VLAN IN PORTS
interface range fastEthernet 0/1-5
switchport mode access 
switchport access vlan 10
exit

interface range fastEthernet 0/6-10
switchport mode access 
switchport access vlan 20
exit

interface range fastEthernet 0/11-15
switchport mode access 
switchport access vlan 30
exit

interface range fastEthernet 0/15-20
switchport mode access 
switchport access vlan 40
exit

interface gigabitEthernet 0/1
switchport mode trunk 

################ L2 SWITCH COMMAND  S/W3 ########################

# ADD VLAN IN PORTS
interface range fastEthernet 0/1-5
switchport mode access 
switchport access vlan 10
exit

interface range fastEthernet 0/6-10
switchport mode access 
switchport access vlan 20
exit

interface range fastEthernet 0/11-15
switchport mode access 
switchport access vlan 30
exit

interface range fastEthernet 0/15-20
switchport mode access 
switchport access vlan 40
exit

interface gigabitEthernet 0/1
switchport mode trunk 




```