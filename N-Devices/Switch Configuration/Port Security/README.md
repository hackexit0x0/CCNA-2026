#### Port Security (Cisco Switches)
> Port Security is used to control which devices (MAC addresses) are allowed to connect to a switch port.

#### Advantages of Port Security
- **Prevents unauthorized access** : Only approved devices can connect to a port.\
- **Limits MAC flooding attacks** : Protects the switch CAM table from overflow.\
- **Improves network security** : Stops users from connecting hubs, switches, or extra devices.\
- **Easy to configure** : Simple CLI commands, no extra hardware needed.\
- **Sticky MAC feature** : Automatically learns MAC addresses and saves them.


### Disadvantages of Port Security
- **Manual management** : MAC address changes require reconfiguration.\
- **Not scalable for large networks** : Difficult to manage many users/devices.\
- **Port can shut down** : Incorrect config may cause loss of connectivity.\
- **Does not encrypt traffic** : Only controls access, not data protection.\
- **MAC spoofing possible** : Attackers can fake MAC addresses.

## Port Security Configuration Commands
> NOTE: Port security works only on Access Ports

### 1. Enable Port Security
```py
Switch(config)# interface fastEthernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport port-security

# 📌 Enables port security on the interface

## Remove port-security
Switch(config-if)# no switchport port-security
```

### 2. MAC Address Limiting
```py
## Set maximum allowed MAC addresses
Switch(config-if)# switchport port-security maximum 2

## 📝 Allows only 2 MAC addresses on this port
```
> Manually Configure a Secure MAC Address
```py
Switch(config-if)# switchport port-security mac-address 000A.1B2C.3D4E
## 📝 Only this MAC address is allowed
```
### 3. Sticky MAC Address
```py
### Enable Sticky MAC Learning
Switch(config-if)# switchport port-security mac-address sticky


## 📝 Switch learns MAC automatically and saves it in running-config
```
> Sticky MAC + Maximum Limit Example
```py
Switch(config-if)# switchport port-security maximum 1
Switch(config-if)# switchport port-security mac-address sticky

##📝 Allows only one dynamically learned MAC address
```

### 4. Violation Modes
> Violation mode defines what happens when an unauthorized device connects.

> A. Protect Mode
```py
Switch(config-if)# switchport port-security violation protect


✔ Drops unauthorized frames
❌ No alert, no log, no shutdown

📝 Silent protection
```
> B. Restrict Mode
```py
Switch(config-if)# switchport port-security violation restrict


✔ Drops frames
✔ Generates syslog message
✔ Increments violation counter

📝 Best for monitoring security events
```
> C. Shutdown Mode (Default)
```py
Switch(config-if)# switchport port-security violation shutdown
✔ Port goes err-disabled
✔ Syslog message generated

📝 Most secure but causes downtime
```
### 5. Aging Timers
> Used to remove learned MAC addresses automatically.

```py
Enable Aging Time

Switch(config-if)# switchport port-security aging time 5

📝 MAC address removed after 5 minutes
```
> Aging Type
```py
# Absolute Aging

Switch(config-if)# switchport port-security aging type absolute

📝 MAC removed after fixed time
```
> Inactivity Aging
```py
Switch(config-if)# switchport port-security aging type inactivity

📝 MAC removed if no traffic is seen
```

### 6. Recovery from Shutdown (Err-disabled)
```py
# Manual Recovery
Switch(config-if)# shutdown
Switch(config-if)# no shutdown
```
> Automatic Recovery
```py
Switch(config)# errdisable recovery cause psecure-violation
Switch(config)# errdisable recovery interval 300

📝 Port recovers automatically after 300 seconds
```

### 7. Verification Commands
```py
Switch# show port-security

# 📝 Displays global port security status

Switch# show port-security interface fastEthernet0/1

# 📝 Detailed port security info

Switch# show running-config interface fastEthernet0/1

#📝 Shows configured MAC addresses
```

### Quick Summary Table
| Feature    | Command                         |
| ---------- | ------------------------------- |
| Enable     | `switchport port-security`      |
| Max MAC    | `maximum`                       |
| Sticky MAC | `mac-address sticky`            |
| Violation  | `protect / restrict / shutdown` |
| Aging      | `aging time / type`             |
| Verify     | `show port-security`            |
