# 🔐 Router Basic Commands & Username–Password Configuration (Step-by-Step)

---

## 🧑‍💻 Why set usernames & passwords?
Router authentication is required to:
- Prevent **unauthorized access**
- Secure **Console, AUX, and VTY (Telnet/SSH)** access
- Protect **Privileged EXEC mode**
- Mandatory for **CCNA labs & real networks**

---

## 🔑 Types of password protection
- **Console password** – Local physical access  
- **AUX password** – Remote administration via AUX port  
- **VTY password** – Telnet / SSH access (remote)  
- **Enable password / enable secret** – Privileged EXEC mode  
- **Local username & password** – Recommended (user-based authentication)

---

# 🧭 Router command modes flow
User Mode → Privileged Mode → Global Config → Line / Interface Mode

> Tip: Use `enable` to move from User to Privileged mode and `configure terminal` to go into Global Config.

---

## 1️⃣ User Mode
Used for basic access only

```text
Router>
Router> enable
```

## 2️⃣ Privileged Mode
Used for monitoring & troubleshooting

```text
Router#
Router# show running-config
Router# show startup-config
Router# show flash
Router# show version
Router# show ip interface brief
Router# configure terminal
```

## 3️⃣ Global Configuration Mode
Used to configure the router

```text
Router(config)#
```

### 🌐 Assign IP Address to Interface

```text
Router(config)# interface <interface-type> <interface-number>
Router(config-if)# ip address <ip-address> <subnet-mask>
Router(config-if)# no shutdown
Router(config-if)# exit
```

---

## 🔐 Password configuration (step-by-step)

### 4️⃣ Set enable secret (RECOMMENDED)
```text
Router(config)# enable secret strongpass
```
- ✅ Encrypted in config
- ⚠️ Do NOT rely on `enable password`; prefer `enable secret`.

### 5️⃣ Create local username
```text
Router(config)# username admin secret admin@123
```

### 6️⃣ Configure console login (use local user)
```text
Router(config)# line console 0
Router(config-line)# login local
Router(config-line)# exit
```

### 7️⃣ Configure AUX port login
```text
Router(config)# line aux 0
Router(config-line)# login local
Router(config-line)# exit
```

### 8️⃣ Configure VTY (Telnet / SSH) login
```text
Router(config)# line vty 0 4
Router(config-line)# login local
Router(config-line)# exit
```

---

## 🔒 (Optional) Traditional line passwords
Not recommended — prefer local username-based login.

Console password:
```text
Router(config)# line con 0
Router(config-line)# password <password>
Router(config-line)# login
Router(config-line)# exit
```

AUX password:
```text
Router(config)# line aux 0
Router(config-line)# password <password>
Router(config-line)# login
Router(config-line)# exit
```

VTY (Telnet) password:
```text
Router(config)# line vty 0 4
Router(config-line)# password <password>
Router(config-line)# login
Router(config-line)# exit
```

---

## 🌐 Secure remote access (SSH — best practice)

### 9️⃣ Set hostname & domain
```text
Router(config)# hostname Router1
Router1(config)# ip domain-name ccna.local
```

### 🔟 Generate RSA key
```text
Router1(config)# crypto key generate rsa
```
- Use key size 2048 or higher (recommended).

### 1️⃣1️⃣ Allow SSH only (disable Telnet)
```text
Router1(config)# line vty 0 4
Router1(config-line)# transport input ssh
Router1(config-line)# login local
Router1(config-line)# exit
```

---

## 🔐 Encrypt plain-text passwords
```text
Router1(config)# service password-encryption
```
- This provides weak reversible encryption; still use `secret` for strong hashing.

---

## 💾 Save configuration (VERY IMPORTANT)
```text
Router# copy running-config startup-config
# OR
Router# write memory
# OR
Router# write
```

---

## 📌 Useful show commands
```text
Router# show running-config
Router# show startup-config
Router# show version
Router# show flash
Router# show ip interface brief
```

---

## ✅ Final summary
- Use **enable secret**, not `enable password`  
- Always prefer **local username** authentication for lines  
- Prefer **SSH** over Telnet for remote access  
- **Save** configuration after changes  
- Follow command order strictly for labs & exams

---

🎯 Best for: CCNA Preparation | Networking Labs | Interview Questions | Real-World Configuration

---

If you want next:
- ✅ **Router Boot Process README**
- ✅ **All CCNA router commands in one file**
- ✅ **Switch + Router combined command book**
- ✅ **Exam-oriented one-page cheat sheet**

Just tell me 👍
