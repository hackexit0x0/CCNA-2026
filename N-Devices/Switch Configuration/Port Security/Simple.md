### Port Down
```py
# Port Down 21 - 24 Port Down
Switch(config)#interface range fastEthernet 0/21 - 24
Switch(config)#shutdown


FastEthernet0/21       unassigned      YES manual administratively down down 
FastEthernet0/22       unassigned      YES manual administratively down down 
FastEthernet0/23       unassigned      YES manual administratively down down 
FastEthernet0/24       unassigned      YES manual administratively down down 


## Up Switch Port
Switch(config)#interface range fastEthernet 0/21 - 24
Switch(config)#no shutdown 

```

### Vlan
```py
Switch(config)#interface range fastEthernet 0/21 - 24
Switch(config-if-range)#switchport mode access 
Switch(config-if-range)#switchport access vlan 555
% Access VLAN does not exist. Creating vlan 555


## Remove Vlan in Ports
Switch(config)# interface range fastEthernet 0/21 - 24
Switch(config-if-range)# no switchport access vlan

```


### show port-security
```py
Switch(config)#interface gigabitEthernet 0/1
Switch(config-if)#switchport port-security 

# if Command Reject Then Excute Thi Commnds
Switch(config)#interface gigabitEthernet 0/1
Switch(config-if)#switchport mode access 
Switch(config-if)#switchport port-security 

### Check Applyed port-security

Switch#show port-security 
Secure Port MaxSecureAddr CurrentAddr SecurityViolation Security Action
               (Count)       (Count)        (Count)
--------------------------------------------------------------------
       Gig0/1        1          0                 0         Shutdown
----------------------------------------------------------------------
Switch#
%LINK-5-CHANGED: Interface GigabitEthernet0/1, changed state to administratively down

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/1, changed state to down


## Remove Port-security
Switch(config)#interface gigabitEthernet 0/1
Switch(config-if)# no switchport port-security

```