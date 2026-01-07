### + IP Address Classes:
```py
Class A: 0.0.0.0 - 127.255.255.255 (large networks) 
Class B: 128.0.0.0 - 191.255.255.255 (medium networks)
Class C: 192.0.0.0 - 223.255.255.255 (small networks)
Class D: 224.0.0.0 - 239.255.255.255 (multicast)
Class E: 240.0.0.0 - 254.255.255.255 (experimental)
```
Class A:
```py
Class A: 
0.0.0.0 - 127.255.255.255 (large networks)
Range : 0.0.0.0 – 127.255.255.255  
Subnet Mask : 255.0.0.0  
Notation : N.H.H.H  
CIDR : /8  
Active Bits : 11111111.00000000.00000000.00000000

# Used for very large networks (big companies, ISPs).
# First octet is Network, remaining three are Host.
# First bit of Class A is always 0, so range starts from 0 — 127.
# Number of networks: 128
# Number of hosts in each network:
# 16,777,214 usable hosts
```
Class B:
```py
Class B: 128.0.0.0 - 191.255.255.255 (medium networks)
Range : 128.0.0.0 – 191.255.255.255  
Subnet Mask : 255.255.0.0  
Notation : N.N.H.H  
CIDR : /16
Active Bits : 11111111.11111111.00000000.00000000

# Used for medium-sized networks (universities, large organizations).
# First two octets = Network, last two = Host.
# First two bits are 10, giving range 128–191.
# Number of networks: 16,384
# Hosts per network: 65,534
```
Class C:
```py
Class C: 192.0.0.0 - 223.255.255.255 (small networks)
Range : 192.0.0.0 – 223.255.255.255  
Subnet Mask : 255.255.255.0  
Notation : N.N.N.H  
CIDR : /24
Active Bits : 11111111.11111111.11111111.00000000

# Used for small networks (small businesses, homes).
# First 3 octets = Network, last octet = Host.
# First three bits are 110 → range 192–223.
# Number of networks: 2,097,152
# Hosts per network: 254
```
Class D:
```py
Class D: 224.0.0.0 - 239.255.255.255 (multicast)
Range : 224.0.0.0 – 239.255.255.255  
Purpose : Multicast (one-to-many communication)

# Not used for normal hosts.
# Used in streaming, conferencing, routing protocols (RIP2, OSPF).
```
Class E:
```py
Class E: 240.0.0.0 - 254.255.255.255 (experimental)
Range : 240.0.0.0 – 254.255.255.255  
Purpose : Research & experimental (not for general use)

# Reserved for future use, experimental testing.
# Rarely used in real networks.
# First four bits are 1111.
```
### + Private IP Addresses:
```py
Class A: 10.0.0.0 - 10.255.255.255
Class B: 172.16.0.0 - 172.31.255.255
Class C: 192.168.0.0 - 192.168.255.255
```
### + Public IP Ranges:
```py
0.0.0.0 - 9.255.255.255
11.0.0.0 - 126.255.255.255
128.0.0.0 - 169.253.255.255
169.255.0.0 - 172.15.255.255
172.32.0.0 - 191.255.255.255
192.0.0.0 - 192.167.255.255
192.169.0.0 - 223.255.255.255
```

### + Loopback IP Addresses:
```py
127.0.0.0 - 127.255.255.255 (used for testing and diagnostics)
```
### + APIPA (Automatic Private IP Addressing):
```py
169.254.0.0 - 169.254.255.255 (used when DHCP server is not available)
```
### + Full Classification (Public + Private + Special)
```py
0.0.0.0 – 0.255.255.255         🔹 Used for default routes
1.0.0.0 – 9.255.255.255         ✔ Public IP range
10.0.0.0 – 10.255.255.255       🔒 Private Range (Class A)
11.0.0.0 – 126.255.255.255      ✔ Public range
127.0.0.0 – 127.255.255.255     🔁 Loopback Most used: 127.0.0.1
128.0.0.0 – 169.253.255.255     ✔ Public range
169.254.0.0 – 169.254.255.255   ⚠ APIPA (Automatic Private IP Addressing) Given when DHCP fails.
169.255.0.0 – 172.15.255.255    ✔ Public range
172.16.0.0 – 172.31.255.255     🔒 Private Range (Class B)
172.32.0.0 – 191.255.255.255    ✔ Public Range
192.0.0.0 – 192.0.0.255         ✔ Special (IANA)
192.0.2.0 – 192.0.2.255         📘 Documentation use only (TEST-NET-1)
192.88.99.0 – 192.88.99.255     ❌ Deprecated (6to4 Relay)
192.168.0.0 – 192.168.255.255   🔒 Private Range (Class C)
192.169.0.0 – 223.255.255.255   ✔ Public Range
224.0.0.0 – 239.255.255.255     📡 Multicast (Class D)
240.0.0.0 – 255.255.255.255     🧪 Experimental (Class E) Not used in public networking.
```