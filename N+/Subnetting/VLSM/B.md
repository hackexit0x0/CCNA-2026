```py
# ============================================================
# 📘 VLSM (Variable Length Subnet Masking) – Class B Example
# ============================================================

# ----------------------------
# Given Information
# ----------------------------

# Class B address format
# N.N.H.H  → Network.Network.Host.Host

MAIN_NETWORK = 172.16.0.0/16   # Original Class B network

# Requirement (Different Host Needs)
# Subnet A → 10,000 Hosts
# Subnet B → 5,000 Hosts
# Subnet C → 2,000 Hosts
# Subnet D → 500 Hosts

# Rule of VLSM:
# 👉 Allocate the subnet with the LARGEST host requirement FIRST

# ============================================================
# Step 1: Calculate Required Prefix for Each Subnet
# ============================================================

# Subnet A: 10,000 Hosts
# 2^14 = 16,384
# Prefix = 32 − 14 = /18

# Subnet B: 5,000 Hosts
# 2^13 = 8,192
# Prefix = /19

# Subnet C: 2,000 Hosts
# 2^11 = 2,048
# Prefix = /21

# Subnet D: 500 Hosts
# 2^9 = 512
# Prefix = /23

# ============================================================
# Step 2: Allocate Subnets (Largest to Smallest)
# ============================================================

# ----------------------------
# Subnet A (/18)
# ----------------------------

# Subnet Mask : 255.255.192.0
# Block Size  : 64 (3rd octet)

# Network     : 172.16.0.0/18
# First IP    : 172.16.0.1
# Last IP     : 172.16.63.254
# Broadcast   : 172.16.63.255
# Usable IPs  : 16,382

# ----------------------------
# Subnet B (/19)
# ----------------------------

# Subnet Mask : 255.255.224.0
# Block Size  : 32 (3rd octet)

# Network     : 172.16.64.0/19
# First IP    : 172.16.64.1
# Last IP     : 172.16.95.254
# Broadcast   : 172.16.95.255
# Usable IPs  : 8,190

# ----------------------------
# Subnet C (/21)
# ----------------------------

# Subnet Mask : 255.255.248.0
# Block Size  : 8 (3rd octet)

# Network     : 172.16.96.0/21
# First IP    : 172.16.96.1
# Last IP     : 172.16.103.254
# Broadcast   : 172.16.103.255
# Usable IPs  : 2,046

# ----------------------------
# Subnet D (/23)
# ----------------------------

# Subnet Mask : 255.255.254.0
# Block Size  : 2 (3rd octet)

# Network     : 172.16.104.0/23
# First IP    : 172.16.104.1
# Last IP     : 172.16.105.254
# Broadcast   : 172.16.105.255
# Usable IPs  : 510

# ============================================================
# Step 3: Final VLSM Summary
# ============================================================

# Subnet | Network        | Prefix | Usable Hosts
# -------|---------------|--------|--------------
# A      | 172.16.0.0    | /18    | 16,382
# B      | 172.16.64.0   | /19    | 8,190
# C      | 172.16.96.0   | /21    | 2,046
# D      | 172.16.104.0  | /23    | 510

# ============================================================
# ✅ End of VLSM – Class B Explanation
# ============================================================
```