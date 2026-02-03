CISCO L2 SWITCH – ENABLE SSH (STEP-BY-STEP WITH EXPLANATION)
====================================================

STEP 1: ENTER CONFIGURATION MODE
--------------------------------
enable
configure terminal

Explanation:
- enable : privileged mode
- configure terminal : global configuration mode

STEP 2: SET HOSTNAME
--------------------
hostname L2-SWITCH-1

Explanation:
- Required for SSH
- Helps identify device

STEP 3: SET DOMAIN NAME
----------------------
ip domain-name docxinfo.local

Explanation:
- Mandatory for RSA key generation

STEP 4: CREATE LOCAL USER
------------------------
username admin privilege 15 secret Admin@123

Explanation:
- admin : username
- privilege 15 : full access
- secret : encrypted password

STEP 5: GENERATE RSA KEY
-----------------------
crypto key generate rsa

When prompted:
How many bits in the modulus [512]: 2048

Explanation:
- Enables SSH
- 2048-bit key is secure

STEP 6: ENABLE SSH VERSION 2
---------------------------
ip ssh version 2
ip ssh time-out 60
ip ssh authentication-retries 3

Explanation:
- SSH v2 is secure

STEP 7: CONFIGURE MANAGEMENT VLAN
--------------------------------
interface vlan 3212
 ip address 10.3.212.10 255.255.255.0
 no shutdown
exit

Explanation:
- Management IP for SSH access

STEP 8: CONFIGURE DEFAULT GATEWAY
--------------------------------
ip default-gateway 10.3.212.1

Explanation:
- Required for remote SSH access

STEP 9: CONFIGURE VTY LINES (SSH ONLY)
-------------------------------------
line vty 0 4
 login local
 transport input ssh
 exec-timeout 10 0
exit

line vty 5 15
 login local
 transport input ssh
exit

Explanation:
- Disables Telnet
- Enables SSH only

STEP 10: SAVE CONFIGURATION
--------------------------
end
write memory

VERIFICATION COMMANDS
--------------------
show ip ssh
show crypto key mypubkey rsa
show ip interface brief
show running-config | section vty

TEST SSH FROM PC
----------------
ssh admin@10.3.212.10

END OF FILE
