# 📐 FLSM (Fixed Length Subnet Masking)
## Corrected Formula & Step-by-Step Explanation
> This document explains **FLSM subnetting** using a **Class C network** with a requirement of **50 hosts per subnet**.

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
- **Network class:** Class C  
- **Default subnet mask:** /24  

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

| Power | Value |
|-----|------|
| 2⁷ | 128 |
| 2⁶ | 64 | >> This Values
| 2⁵ | 32 |
| 2⁴ | 16 |
| 2³ | 8 |
| 2² | 4 |
| 2¹ | 2 |
| 2⁰ | 1 |

```
### 2️⃣ Find Subnet (Network) Bits
```py
Class C provides:
Total bits = 8 Bits(11111111.11111111.11111111.00000000)
Host bits = 6 
Subnet bits = 8 − 6 = 2


____________________________
## Subnet bits (n) = 2**   
```
### 3️⃣ Calculate New CIDR
```py
Default Class C prefix:
/24



Add subnet bits:
24 + 2 = /26  Bits(11111111.11111111.11111111.11000000)
                                              ^^

## New CIDR = /26
```

### 4️⃣ Subnet Mask Calculation
```py
Subnet bits = 2  
Binary calculation:
128 + 64 = 192

## Subnet Mask = 255.255.255.192
```

### 5️⃣ Block Size Calculation
```py
**Formula:**
# Block Size = 256 − Subnet Mask Value



# Calculation:
256 − 192 = 64

## Block Size = 64
```

### 6️⃣ Total Number of Subnets
```py
**Formula:**
2^n


Calculation:
2^2 = 4

# Total Subnets = 4

```

### 7️⃣ Hosts per Subnet
```py
**Formula:**
2^h − 2


# Calculation:
2^6 − 2 = 62

```
### FLSM Subnet Details (/26)

| Subnet # | Network ID    | Subnet Mask     | First IP      | Last IP       | Broadcast IP  |
| -------- | ------------- | --------------- | ------------- | ------------- | ------------- |
| 1        | 192.168.1.0   | 255.255.255.192 | 192.168.1.1   | 192.168.1.62  | 192.168.1.63  |
| 2        | 192.168.1.64  | 255.255.255.192 | 192.168.1.65  | 192.168.1.126 | 192.168.1.127 |
| 3        | 192.168.1.128 | 255.255.255.192 | 192.168.1.129 | 192.168.1.190 | 192.168.1.191 |
| 4        | 192.168.1.192 | 255.255.255.192 | 192.168.1.193 | 192.168.1.254 | 192.168.1.255 |


---
```py
## Usable hosts per subnet = 62

## ✔ Enough for the required **50 hosts**


## 📊 Final Summary Table

| Item | Value |
|----|------|
| Required Hosts | 50 |
| Host Bits (h) | 6 |
| Subnet Bits (n) | 2 |
| New CIDR | /26 |
| Subnet Mask | 255.255.255.192 |
| Block Size | 64 |
| Total Subnets | 4 |
| Hosts per Subnet | 62 |

```

## 🧠 Key Subnetting Formulas (Remember These)
```
### Host Calculation
2^h − 2 ≥ Hosts


### Subnet Calculation
New Prefix = Default Prefix + Subnet Bits



### Block Size
256 − Subnet Mask Value

```
### ✅ Conclusion
> This FLSM design successfully meets the requirement of **50 hosts per subnet**, using a **/26 subnet mask**, providing **4 equal-sized subnets** with **62 usable hosts each**.

