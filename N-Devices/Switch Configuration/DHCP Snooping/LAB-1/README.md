Router>enable
Router#configure terminal
Router(config)#interface GigabitEthernet0/0/0
Router(config-if)#ip address 192.168.10.1 255.255.255.0
Router(config-if)#ip address 192.168.10.1 255.255.255.0
Router(config-if)#no shutdown

Router(config)#ip dhcp excluded-address 192.168.10.1 192.168.10.5
Router(config)#ip dhcp pool hsv.io
Router(dhcp-config)#network 192.168.10.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.10.1
Router(dhcp-config)#dns-server 8.8.8.8