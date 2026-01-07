# 🔐 Enable SSH on Cisco Router

This guide explains how to enable **SSH access** on a Cisco router step by step.

---

#### Enter Privileged & Global Configuration Mode
```bash
Router> enable
Router# configure terminal

## Set Hostname (Required for SSH)
Router(config)# hostname R1

## Set Domain Name (Required for SSH)
R1(config)# ip domain-name lab.local

## Create Local User
R1(config)# username admin privilege 15 secret admin@123

## Generate RSA Key
R1(config)# crypto key generate rsa
> When prompted:
> How many bits in the modulus [512]: 2048

## Enable SSH Version 2
R1(config)# ip ssh version 2

## Configure VTY Lines for SSH Only
R1(config)# line vty 0 4
R1(config-line)# login local
R1(config-line)# transport input ssh
R1(config-line)# exit

## (Optional but Recommended) Set Enable Secret
R1(config)# enable secret enable@123

## Save Configuration

R1# write memory
```

> Verify SSH
```py
R1# show ip ssh
R1# show crypto key mypubkey rsa
```

> SSH Login from PC
```py
ssh admin@<router-ip>

ssh -l admin 10.0.0.1
```

> ⚠️ Common Issues
- ❌ No hostname or domain name → SSH won’t work
- ❌ RSA key not generated → SSH fails
- ❌ VTY set to Telnet → SSH blocked

#### 📌 NOTE: 
- Works on **Cisco IOS Routers**
- Tested on **GNS3 / Packet Tracer**
- Use strong passwords in production
