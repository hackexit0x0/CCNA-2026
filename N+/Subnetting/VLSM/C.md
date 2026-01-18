```py
# ============================================================
# 📘 VLSM (Variable Length Subnet Masking) – Class C Example
# ============================================================

# ----------------------------
# Given Information
# ----------------------------

# Class C address format
# N.N.N.H  → Network.Network.Network.Host

MAIN_NETWORK = 192.168.1.0/24   # Original Class C network

# Requirement (Different Host Needs)
# Subnet A → 50 Hosts
# Subnet B → 25 Hosts
# Subnet C → 10 Hosts
# Subnet D → 2 Hosts

# Rule of VLSM:
# 👉 Always allocate the subnet with the LARGEST host requirement FIRST

# ============================================================
# Step 1: Calculate Required Prefix for Each Subnet
# ============================================================

# Subnet A: 50 Hosts
# 2^6 = 64
# Prefix = 32 − 6 = /26

# Subnet B: 25 Hosts
# 2^5 = 32
# Prefix = /27

# Subnet C: 10 Hosts
# 2^4 = 16
# Prefix = /28

# Subnet D: 2 Hosts
# 2^2 = 4
# Prefix = /30

# ============================================================
# Step 2: Allocate Subnets (Largest to Smallest)
# ============================================================

# ----------------------------
# Subnet A (/26)
# ----------------------------

# Subnet Mask : 255.255.255.192
# Block Size  : 64 (4th octet)

# Network     : 192.168.1.0/26
# First IP    : 192.168.1.1
# Last IP     : 192.168.1.62
# Broadcast   : 192.168.1.63
# Usable IPs  : 62

# ----------------------------
# Subnet B (/27)
# ----------------------------

# Subnet Mask : 255.255.255.224
# Block Size  : 32 (4th octet)

# Network     : 192.168.1.64/27
# First IP    : 192.168.1.65
# Last IP     : 192.168.1.94
# Broadcast   : 192.168.1.95
# Usable IPs  : 30

# ----------------------------
# Subnet C (/28)
# ----------------------------

# Subnet Mask : 255.255.255.240
# Block Size  : 16 (4th octet)

# Network     : 192.168.1.96/28
# First IP    : 192.168.1.97
# Last IP     : 192.168.1.110
# Broadcast   : 192.168.1.111
# Usable IPs  : 14

# ----------------------------
# Subnet D (/30)
# ----------------------------

# Subnet Mask : 255.255.255.252
# Block Size  : 4 (4th octet)

# Network     : 192.168.1.112/30
# First IP    : 192.168.1.113
# Last IP     : 192.168.1.114
# Broadcast   : 192.168.1.115
# Usable IPs  : 2

# ============================================================
# Step 3: Final VLSM Summary
# ============================================================

# Subnet | Network          | Prefix | Usable Hosts
# -------|------------------|--------|--------------
# A      | 192.168.1.0      | /26    | 62
# B      | 192.168.1.64     | /27    | 30
# C      | 192.168.1.96     | /28    | 14
# D      | 192.168.1.112    | /30    | 2

# ============================================================
# ✅ End of VLSM – Class C Explanation
# ============================================================
```