# INTRODUCTION TO ROUTERS

---

### 📘 What is a Router?
> A **router** is a device which makes communication possible between **two or more different networks** present in the same or different geographical locations.

- It is an **internetworking device** used to connect two or more different networks
- It works on **Layer 3 (Network Layer)** of the OSI Model

---

#### ⚙️ Functions of a Router
> A router performs **two basic functions**:

- **Selects the best path** from the routing table
- **Forwards the packet** on that selected path

---

#### 🏭 Other Vendors Apart from Cisco
Many companies manufacture routers, such as:
```py
- Nortel
- Multicom
- Cyclades
- Juniper
- D-Link
- Linksys
- 3Com
```

### 🧩 Router Classification
```py
 _________________________________ _________________________________
|      FIXED ROUTER               | MODULAR ROUTER                  |
|---------------------------------|---------------------------------|
| Non-Upgradeable                 | Upgradeable                     |
| Cannot add/remove interfaces    | Interfaces can be added/removed |
| No slots available              | Slots depend on router series   |
|_________________________________|_________________________________|
```

#### 📌 Example of Modular Router
- Upgradeable hardware
- Supports multiple interface modules
- Used in enterprise and large networks

---

#### 📌 Example of Fixed Router
- Interfaces are predefined
- Cannot be upgraded

**Visible Components:**
- AUI (Attachment Unit Interface)
- Serial Ports (S0, S1)
- Console Port (Con 0)
- Auxiliary Port (Aux 0)
- Power Switch
- Power Supply

---

#### 🔌 External Ports of Router

### 🌐 WAN Interfaces
> Used to connect **remote networks**.

- **Serial Interface**
  - Examples: S0, S1
  - Connector: 60-pin / 26-pin (Smart Serial)

- **ISDN Interface**
  - Example: BRI
  - Connector: RJ-45

---

### 🖧 LAN Interfaces (Ethernet)
> Used to connect **local networks**.

- **AUI (Attachment Unit Interface)**
  - Example: E0
  - Connector: 15-pin

- **10Base-T Ethernet**
  - Connector: RJ-45

---

### 🛠️ Administration Interfaces

- **Console Port**
  - RJ-45
  - Used for Local Administration

- **Auxiliary Port**
  - RJ-45
  - Used for Remote Administration

---

#### `2601` Model Router (Modular Router)

##### 🔧 Router Interface Overview
> The **Cisco 2601** is a modular router supporting:

- Serial Ports
- FastEthernet Ports
- Console Port
- Auxiliary Port
- Power Switch
- Power Cord Connection


#### 🔌 Attachment Unit Interface (AUI)

- 15-pin female connector
- Also called:
  - Ethernet Port
  - LAN Port
  - Default Gateway Port
- Used for LAN connectivity
- Requires a **Transceiver** (RJ-45 to 15-pin)

---

#### 🌐 Serial Port

- 60-pin female (15 pins × 4 rows)
- Smart Serial: 26-pin female
- WAN Port
- Used to connect remote locations
- **V.35 Cable**:
  - One end: 60-pin male
  - Other end: 18-pin male

---

#### 🖥️ Console Port

- Local Administrative Port
- Used for:
  - Initial Configuration
  - Password Recovery
  - Local Administration
- Connector: RJ-45
- IMPORTANT: Most delicate port on the router

---

#### 🔌 Console Connectivity

#### Steps
1. Connect rollover cable to router Console Port (RJ-45)
2. Connect other end to RJ-45 to DB-9 converter
3. Attach DB-9 to PC Serial Port
4. Open terminal emulation software

---

#### 🛠️ Auxiliary Port

- Remote Administrative Port
- Used for remote administration
- Uses RJ-45
- Console or rollover cable required

---

#### ⚙️ Internal Components of Router

#### ROM
- Contains Bootstrap Program
- Similar to PC BIOS
- Bootstrap version: 1.10

#### Flash
- Stores Cisco IOS
- IOS provides CLI interface

#### NVRAM
- Non-Volatile RAM
- Stores Startup Configuration
- Permanent Storage
- Typical size: 32 KB

#### RAM
- Temporary Storage
- Stores Running Configuration
- Minimum size: 2 MB
- Larger than NVRAM

#### Processor
- Controls all router operations
- Handles routing and packet forwarding

---

#### 🔁 Router Start-Up Sequence

1. Bootstrap loaded from ROM
2. POST is executed
3. IOS located in Flash
4. IOS loaded into RAM
5. Startup-config searched in NVRAM
6. Configuration loaded into RAM

---

#### 🧭 Router Modes

##### User Mode
- Basic monitoring only

##### Privileged Mode
- Monitoring and troubleshooting

##### Global Configuration Mode
- Affects entire router

##### Interface Mode
- Configuration of specific interface

##### ROMMON Mode
- Password recovery
- Low-level troubleshooting

---

#### 🖥️ Console Connectivity (OS Wise)

##### IN WINDOWS
- Start → Programs → Accessories → Communications
- Open HyperTerminal
- Select Serial (COM Port)
- Restore Port Defaults

#### IN LINUX
`minicom -s`

#### 🎯 Useful For
- CCNA Exam Preparation
- Router Hardware Understanding
- Practical Labs
- Interview Revision
