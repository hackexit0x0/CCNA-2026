### Enable Telnet on Cisco Router

#### What is Telnet?
> **Telnet** is a remote management protocol used to access a router or switch CLI over a network.

> ⚠️ **Note:** Telnet sends data in **plain text** (not secure).  
> For real networks, **SSH is recommended**, but Telnet is still important for **CCNA labs & basics**.

---

#### Network Example
- **Router IP:** 192.168.1.1  
- **Client Network:** 192.168.1.0/24  



#### Configure IP Address on Router Interface
```py
Router> enable
Router# configure terminal

#(Recommended) Create Local Username
Router(config)# username admin password admin123


Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

# ✅ This IP will be used to access Telnet
```

#### SET ENABLE PASSWORD
```py
Router(config)# enable password cisco
```

---

#### Configure VTY Lines for Telnet
```py
Router(config)# line vty 0 4
Router(config-line)# password telnet123
Router(config-line)# login
Router(config-line)# transport input telnet
Router(config-line)# exit

# ➡️ Allows remote Telnet access to the router.
```



---



---

#### Enable Telnet with Local Authentication
```py
Router(config)# line vty 0 4
Router(config-line)# login local
Router(config-line)# transport input telnet
Router(config-line)# exit
```

---

#### Save Configuration
```py
Router# write memory
```

---

#### ✅ Telnet Configuration DONE 🎉

> Verify Telnet Configuration
```py
Router# show running-config | section vty
```

---

#### 🔹 Client Side (PC)
```js
1. Set IP address in same network (192.168.1.x)
2. Open Command Prompt
```
> Access in PC
```py
telnet 192.168.1.1

- **Username:** admin  
- **Password:** admin123  
```


### Common Interview Questions (Quick)

> Q1. Which protocol is more secure: Telnet or SSH?\
`➝ SSH`

> Q2. Default VTY lines in Cisco router?\
`0 to 4`

> Q3. Telnet uses which port?\  
`TCP Port 23`

> Q4. Why Telnet is not secure\  
`Data is sent in plain text`
