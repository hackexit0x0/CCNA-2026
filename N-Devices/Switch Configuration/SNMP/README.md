### SNMP (Simple Network Management Protocol) – Complete Guide with Cisco Commands

> This document explains **what SNMP is**, **how it works**, and **how to configure SNMP on Cisco routers and switches** using CLI commands.

---

## 📌 What is SNMP?

**SNMP (Simple Network Management Protocol)** is used to **monitor, manage, and receive alerts** from network devices such as:

- Routers
- Switches
- Firewalls
- Servers

SNMP helps administrators monitor:
- CPU usage
- Memory usage
- Interface status (up/down)
- Bandwidth utilization
- Device health



### 📌 SNMP Components

#### 1️⃣ SNMP Manager
- Monitoring system (e.g., Zabbix, PRTG, SolarWinds)
- Sends requests and receives alerts

#### 2️⃣ SNMP Agent
- Runs on routers and switches
- Collects device information

#### 3️⃣ MIB (Management Information Base)
- Database containing device information
- Example: interfaces, CPU, memory, traffic stats

---

#### 📌 How SNMP Works
```py
SNMP Manager → GET / SET request
SNMP Agent → RESPONSE

SNMP Agent → TRAP (Alert)
SNMP Manager → Receives alert
```

---

## 📌 SNMP Versions

| Version | Security | Description |
|------|---------|------------|
| SNMPv1 | ❌ Low | Old and insecure |
| SNMPv2c | ⚠ Medium | Community-based |
| SNMPv3 | ✅ High | Authentication + Encryption |

✅ **SNMPv3 is recommended for production networks**

---

### 📌 SNMP Ports
```py
| Service | Port |
|------|------|
| SNMP GET / SET | UDP 161 |
| SNMP TRAP | UDP 162 |
```

### 🔹 SNMP Configuration on Cisco Devices

---

### 🔹 1️⃣ SNMPv2 Configuration (Basic / Lab Use)

```py
enable
configure terminal
snmp-server community public RO
# RO → Read Only

snmp-server community private RW
# RW → Read & Write\


# Opthe Command 
snmp-server community read ro
snmp-server community write rw
```

### 2️⃣ SNMPv3 Configuration (Secure – Recommended)
```py
# Step 1: Create SNMP Group
snmp-server group NMS v3 priv

# Step 2: Create SNMP User
snmp-server user snmpadmin NMS v3 auth sha Auth@123 priv aes 128 Priv@123
```
### 🔹 3️⃣ Configure SNMP Trap Destination
```py
snmp-server host 192.168.10.50 version 3 priv snmpadmin
snmp-server enable traps

# 192.168.10.50 → SNMP Manager IP
```

### 4️⃣ Add Device Information
```py
snmp-server location DataCenter-Rack1
snmp-server contact admin@company.com
```

### 📌 SNMP in Your Network Topology
```py
Device	SNMP Role
Router (ISR4331)	SNMP Agent
Multilayer Switch (3560)	SNMP Agent
Access Switch (2960)	SNMP Agent
Monitoring Server	SNMP Manager
```
### 🔹 Verification Commands
```py
show snmp
show snmp user
show snmp group
```

> 📌 Common SNMP Use Cases
- Interface up/down alerts
- CPU & memory monitoring
- Bandwidth monitoring
- Network performance dashboards
- Fault detection


> 📌 SNMP Interview Questions (Quick)

> Q : Why is SNMPv3 better? \
> ANS :  A: It provides authentication and encryption.

> Q: What is MIB?\
> ANS : A: A database of managed objects.

> Q: SNMP ports?\
> ANS : A: UDP 161 and UDP 162.