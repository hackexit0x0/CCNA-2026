### 🔐 Router Basic Commands & Username–Password Configuration (Step-by-Step)

---

### 🧑‍💻 Why Set Username & Password?
Router authentication is required to:
- Prevent **unauthorized access**
- Secure **Console, AUX, and VTY (Telnet/SSH)** access
- Protect **Privileged EXEC mode**
- Mandatory for **CCNA labs & real networks**

---

#### 🔑 Types of Password Protection
- **Console Password** – Local physical access
- **AUX Password** – Remote administration
- **VTY Password** – Telnet / SSH access
- **Enable Password / Enable Secret** – Privileged EXEC mode
- **Local Username & Password** – Recommended (User-based authentication)

---

## 🖥️ BASIC ROUTER COMMANDS

### 🔹 User Mode
```py
Router>
Router> enable
```
#### PRIVILEGED MODE
> Used for monitoring & troubleshooting
```py
Router#
Router# show running-config
Router# show startup-config
Router# show flash
Router# show version
Router# show ip interface brief
Router# configure terminal
```

#### Global configuration mode:
```py
Router(config) #
```
#### Assigning ip address to Ethernet interface:
```py
Router(config) # interface <interface type> <interface no>
Router(config-if) # ip address <ip address> <subnet mask> (Interface Mode)
Router(config-if) # no shut
```

### 🔐 PASSWORD CONFIGURATION (STEP-BY-STEP) 
#### Set Enable Secret (RECOMMENDED)
```py
Router(config)# enable secret strongpass
```