### Cisco Packet Tracer Lab – Static PAT with Two Private Servers
> This lab demonstrates how to configure **Static PAT (Port Address Translation)** on a Cisco router to publish **two private web servers** using **one public IP** with different ports.

<img src="image.png">


### 🖧 STEP 1: Configure Servers (Packet Tracer)

### Server 1 (Web Server)
```py
Service:
HTTP → ON
Server 1 (Web Server)
IP Address : 192.168.10.2
Subnet Mask: 255.255.255.0
Gateway    : 192.168.10.1

Service:
HTTP → ON
Server 2 (Web Server)
IP Address : 192.168.10.3
Subnet Mask: 255.255.255.0
Gateway    : 192.168.10.1

Service:
HTTP → ON
Optional: Edit index.html on each server so you can easily identify which server is being accessed.
```
### 🧠 STEP 2: Router Configuration (CLI)
```py
# Configure Inside Interface (Private)
enable
configure terminal
Configure Inside Interface (LAN)
interface g0/0
 ip address 192.168.10.1 255.255.255.0
 ip nat inside
 no shutdown

# Configure Outside Interface (Public)
interface g0/1
 ip address 10.0.0.1 255.255.255.0
 ip nat outside
 no shutdown
```
### 🔁 STEP 3: Static PAT (Port Forwarding)
```py

SERVER 1 : 192.168.10.2  --|                           |--- http://10.0.0.1:8080  WEB : 1
                            ==> Public ip 10.0.0.1  ==
SERVER 2 : 192.168.10.3  --|                           |--- http://10.0.0.1:9090  WEB : 2
```                          
```py
# Server 1 → Public IP 10.0.0.11 (Port 80)
ip nat inside source static tcp 192.168.10.2 80 10.0.0.1 8080

# Server 2 → Public IP 10.0.0.1 (Port 9090)
ip nat inside source static tcp 192.168.10.3 80 10.0.0.1 9090
```
> ✅ This configuration allows two internal servers to be accessed from the internet using one router and PAT.

#### 🧪 STEP 4: Testing
> From an outside PC, open a web browser:

```py
http://10.0.0.1:8080
→ Server 1 Web Page

http://10.0.0.1:9090
→ Server 2 Web Page
```

🔍 STEP 5: Verification Commands
> Run the following commands on the router:
```py
show ip nat translations
show ip nat statistics
```
