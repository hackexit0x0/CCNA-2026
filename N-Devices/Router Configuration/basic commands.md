### BASIC COMMANDS
#### User mode:
```py
Router >
Router > enable
```

#### Privilege mode:
```py
Router # show running-config
Router # show startup-config
Router # show flash
Router # show version
Router #show ip interface brief
Router # configure terminal ( to enter in Global configuration mode)
```

#### Global configuration mode:
```py
Router(config) #
Assigning ip address to Ethernet interface:
Router(config) # interface <interface type> <interface no>
Router(config-if) # ip address <ip address> <subnet mask> (Interface Mode)
Router(config-if) # no shut
```



#### Assigning console password:
```py
Router(config) # line con 0
Router(config-line) # login (line mode)
Router(config-line) # password <password>
Router(config-line) # exit
Router(config) # exi
```
#### Assigning Auxiliary password:
```py
Router(config) # line aux 0
Router(config-line) # login (line mode)
Router(config-line) # password <password>
Router(config-line) # exit
Router(config) # exit
```

#### Create Local User
```py
Router(config)# username admin secret admin@123
```
#### Apply Username Authentication to Console
```py
Router(config)# line console 0
Router(config-line)# login local
Router(config-line)# exit

```

#### Assigning enable password:
```py
Router(config) # enable secret <password> (To encrypt the password)
Router(config) # enable password <password>
```

#### Assigning Telnet password:
```py
Router(config) # line vty 0 4
Router(config-line) #login (line mode)
Router(config-line) #password <password>
Router(config-line) #exit
Router(config) #exit
```


#### Show commands:
```py
Router # show running-config
Router # show startup-config
Router # show version
Router # show flash
```

#### Commands to save the configuration:
```py
Router # copy running-config startup-config
( OR )
Router # write memory
( OR )
Router # write
```