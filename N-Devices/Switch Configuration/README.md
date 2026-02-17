### SWITCH IMGES

> S3700-24T4F
<img src="img-dev/S3700-24T4F.png">

### Basic Device Identity & Security
> First, enter Global Configuration mode by typing configure terminal (or conf t).

> Hostname
```py
hostname YourSwitchName
```
> Banner Message (The legal warning shown at login)
```py
banner motd #Enter text here, then end with the same character#
```
> Enable Secret Password (Encrypts access to privileged mode)
```py
enable secret YourStrongPassword
```
> Service Password Encryption (Encrypts plain-text passwords in the config file)
```py
service password-encryption
```
### Access Security (Console & VTY)
> Console Password
```py
line console 0
 password <YourConsolePassword>
 login
exit
```
> VTY Passwords (For remote access, usually lines 0-15)
```py
line vty 0 15
 password <YourConsolePassword>
 login
exit
```
### Management VLAN & IP Connectivity
> Management VLAN (SVI)
+ Typically, VLAN 1 is the default, but it's best practice to use a specific management VLAN.
```py
interface vlan 1
 ip address 192.168.1.10 255.255.255.0
 no shutdown
exit
```
### Default Gateway
+ This is essential if you want to manage the switch from a different network/VLAN.
```py
ip default-gateway 192.168.1.1
```
