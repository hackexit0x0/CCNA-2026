# 📐 FLSM (Fixed Length Subnet Masking)
## Corrected Formula & Step-by-Step Explanation
> This document explains **FLSM subnetting** using a **Class B network** with a requirement of **50 hosts per subnet**.

---

## 🔑 Powers of 2 Table

| Power | Value |
|-----|------|
| 2⁷ | 128 |
| 2⁶ | 64 |
| 2⁵ | 32 |
| 2⁴ | 16 |
| 2³ | 8 |
| 2² | 4 |
| 2¹ | 2 |
| 2⁰ | 1 |

---

## 🧮 Network Requirements

- **Required hosts per subnet:** 50  
- **Subnetting method:** FLSM (same size subnet for all networks)  
- **Network class:** Class B  
- **Default subnet mask:** /16  

---

## ✅ Step-by-Step Correct Method

---

### 1️⃣ Find Host Bits (h)
```py
## Usable host formula

2^h − 2 ≥ Required Hosts


# Check values:

2^5 − 2 = 30 ❌
2^6 − 2 = 62 ✅

# Host bits (h) = 6
```
### 2️⃣ Find Subnet (Network) Bits
```py
Class B provides:
Total host bits = 16
Host bits required = 6

Subnet bits = 16 − 6 = 10


## Subnet bits (n) = 10
```
### 3️⃣ Calculate New CIDR
```py

Default Class B prefix:
/16

Add subnet bits:
16 + 10 = /26


## New CIDR = /26
```
### 4️⃣ Subnet Mask Calculation
```py
Binary for /26:
11111111.11111111.11111111.11000000

Decimal calculation:
128 + 64 = 192


## Subnet Mask = 255.255.255.192
```
### 5️⃣ Block Size Calculation
```py
## Formula:
Block Size = 256 − Subnet Mask Value

Calculation:
256 − 192 = 64


## Block Size = 64
```
### 6️⃣ Total Number of Subnets
```py
## Formula:
2^n

Calculation:
2^10 = 1024

## Total Subnets = 1024

# Calculate 2^10 step by step

2 * 2      # 2 × 2 = 4
4 * 2      # 4 × 2 = 8
8 * 2      # 8 × 2 = 16
16 * 2     # 16 × 2 = 32
32 * 2     # 32 × 2 = 64
64 * 2     # 64 × 2 = 128
128 * 2    # 128 × 2 = 256
256 * 2    # 256 × 2 = 512
512 * 2    # 512 × 2 = 1024

2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2
```
### 7️⃣ Hosts per Subnet
```py
## Formula:
2^h − 2

Calculation:
2^6 − 2 = 62


## Usable hosts per subnet = 62
```
### 🌐 FLSM Subnet Details (/26)
> Example Class B Network: 172.16.0.0/16

| Subnet # | Network ID   | Subnet Mask     | First IP     | Last IP      | Broadcast IP |
| -------- | ------------ | --------------- | ------------ | ------------ | ------------ |
| 1        | 172.16.0.0   | 255.255.255.192 | 172.16.0.1   | 172.16.0.62  | 172.16.0.63  |
| 2        | 172.16.0.64  | 255.255.255.192 | 172.16.0.65  | 172.16.0.126 | 172.16.0.127 |
| 3        | 172.16.0.128 | 255.255.255.192 | 172.16.0.129 | 172.16.0.190 | 172.16.0.191 |
| 4        | 172.16.0.192 | 255.255.255.192 | 172.16.0.193 | 172.16.0.254 | 172.16.0.255 |


> 📊 Final Summary Table

| Item             | Value           |
| ---------------- | --------------- |
| Required Hosts   | 50              |
| Host Bits (h)    | 6               |
| Subnet Bits (n)  | 10              |
| New CIDR         | /26             |
| Subnet Mask      | 255.255.255.192 |
| Block Size       | 64              |
| Total Subnets    | 1024            |
| Hosts per Subnet | 62              |


## 🧠 Key Subnetting Formulas (Remember These)
```py
Host Calculation
2^h − 2 ≥ Hosts

Subnet Calculation
New Prefix = Default Prefix + Subnet Bits

Block Size
256 − Subnet Mask Value
```

---

If you want next, I can also give:
- ✅ **Class A FLSM (same format)**
- 🔄 **Class B VLSM**
- 🧠 **1-page subnetting cheat sheet**
- 🧪 **CCNA exam practice problems**

Just tell me 💪

