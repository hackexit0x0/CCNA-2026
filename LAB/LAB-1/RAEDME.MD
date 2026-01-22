


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
## ISP ROUTERS

```py
        ISP PMS                     ISP PSS
     (Public ISP)               (Public ISP)
        |                           |
   203.0.113.1/30             198.51.100.1/30
        |                           |
        |                           |
     G0/0                        G1/0
        \                         /
         \                       /
           Office Router (S-GW)
                G4/0
          LAN: 10.1.50.0/24
          GW : 10.1.50.1

| ISP     | Network         | Router IP    | Office IP    |
| ------- | --------------- | ------------ | ------------ |
| ISP PMS | 203.0.113.0/30  | 203.0.113.1  | 203.0.113.2  |
| ISP PSS | 198.51.100.0/30 | 198.51.100.1 | 198.51.100.2 |


## ISP PMS Router

enable
configure terminal

interface gigabitEthernet0/0
 ip address 203.0.113.1 255.255.255.252
 no shutdown


## ISP PSS Router
enable
configure terminal

interface gigabitEthernet0/0
 ip address 198.51.100.1 255.255.255.252
 no shutdown

## Office Router – WAN Interfaces

### 🔹 ISP PMS (Primary)
enable
configure terminal

interface gigabitEthernet0/0
 ip address 203.0.113.2 255.255.255.252
 no shutdown

### 🔹 ISP PSS (Backup)
interface gigabitEthernet1/0
 ip address 198.51.100.2 255.255.255.252
 no shutdown

 ✔ Green light = interface UP
🟡 Yellow = still negotiating (wait 5–10 sec)

## Default Routes (MOST IMPORTANT) NOT SUPRTED ROUTER
# Primary Route (ISP PMS)
ip route 0.0.0.0 0.0.0.0 203.0.113.1

# ✔ Backup Route (ISP PSS)
ip route 0.0.0.0 0.0.0.0 198.51.100.1 10

## 🧩 CORRECT IP SLA CONFIG (USING ISP GATEWAY)
----------------------------------------------------
## 🔹 Primary ISP (PMS)
ip sla 1
 icmp-echo 203.0.113.1 source-interface gigabitEthernet0/0
 frequency 5
ip sla schedule 1 life forever start-time now

track 1 ip sla 1 reachability

ip route 0.0.0.0 0.0.0.0 203.0.113.1 track 1

## 🔹 Backup ISP (PSS) – Optional Monitoring
ip sla 2
 icmp-echo 198.51.100.1 source-interface gigabitEthernet1/0
 frequency 5
ip sla schedule 2 life forever start-time now

-------------------------------------------------------


## VLAN ACL 
! ACLs
! VLAN 10 - Full Access
ip access-list extended VLAN10-ACL
 permit ip 10.10.10.0 0.0.0.255 any

! VLAN 20 - Intranet Only
ip access-list extended VLAN20-ACL
 permit ip 10.10.20.0 0.0.0.255 172.16.0.3 0.0.0.0
 deny ip 10.10.20.0 0.0.0.255 any

! VLAN 30 - Intranet + Internet
ip access-list extended VLAN30-ACL
 permit ip 10.10.30.0 0.0.0.255 172.16.0.3 0.0.0.0
 permit ip 10.10.30.0 0.0.0.255 any

! VLAN 40 - Web + Internet Only (No Intranet)
ip access-list extended VLAN40-ACL
 permit tcp 10.10.40.0 0.0.0.255 any eq 80
 permit tcp 10.10.40.0 0.0.0.255 any eq 443
 permit ip 10.10.40.0 0.0.0.255 any
 deny ip 10.10.40.0 0.0.0.255 172.16.0.3 0.0.0.0

! Apply ACLs to VLAN interfaces
interface Vlan10
 ip access-group VLAN10-ACL in
interface Vlan20
 ip access-group VLAN20-ACL in
interface Vlan30
 ip access-group VLAN30-ACL in
interface Vlan40
 ip access-group VLAN40-ACL in

```
