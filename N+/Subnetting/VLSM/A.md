```py
# ============================================================
# 📘 VLSM (Variable Length Subnet Masking) – Class A Example
# ============================================================

# ----------------------------
# Given Information
# ----------------------------

# Class A address format
# N.H.H.H  → Network.Host.Host.Host

MAIN_NETWORK = 10.0.0.0/8   # Original Class A network

# Requirement (Different Host Needs)
# Subnet A → 500,000 Hosts
# Subnet B → 200,000 Hosts
# Subnet C → 50,000 Hosts
# Subnet D → 10,000 Hosts

# Rule of VLSM:
# Always allocate subnet with LARGEST host requirement FIRST

# ============================================================
# Step 1: Calculate Required Prefix for Each Subnet
# ============================================================

# Subnet A: 500,000 Hosts
# 2^19 = 524,288 (Enough)
# Prefix = 32 − 19 = /13

# Subnet B: 200,000 Hosts
# 2^18 = 262,144
# Prefix = /14

# Subnet C: 50,000 Hosts
# 2^16 = 65,536
# Prefix = /16

# Subnet D: 10,000 Hosts
# 2^14 = 16,384
# Prefix = /18

# ============================================================
# Step 2: Allocate Subnets (Largest to Smallest)
# ============================================================

# ----------------------------
# Subnet A (/13)
# ----------------------------

# Subnet Mask : 255.248.0.0
# Block Size  : 256 − 248 = 8 (2nd octet)

# Network     : 10.0.0.0/13
# First IP    : 10.0.0.1
# Last IP     : 10.7.255.254
# Broadcast   : 10.7.255.255
# Usable IPs  : 524,286

# ----------------------------
# Subnet B (/14)
# ----------------------------

# Subnet Mask : 255.252.0.0
# Block Size  : 4 (2nd octet)

# Network     : 10.8.0.0/14
# First IP    : 10.8.0.1
# Last IP     : 10.11.255.254
# Broadcast   : 10.11.255.255
# Usable IPs  : 262,142

# ----------------------------
# Subnet C (/16)
# ----------------------------

# Subnet Mask : 255.255.0.0
# Block Size  : 1 (2nd octet)

# Network     : 10.12.0.0/16
# First IP    : 10.12.0.1
# Last IP     : 10.12.255.254
# Broadcast   : 10.12.255.255
# Usable IPs  : 65,534

# ----------------------------
# Subnet D (/18)
# ----------------------------

# Subnet Mask : 255.255.192.0
# Block Size  : 64 (3rd octet)

# Network     : 10.13.0.0/18
# First IP    : 10.13.0.1
# Last IP     : 10.13.63.254
# Broadcast   : 10.13.63.255
# Usable IPs  : 16,382

# ============================================================
# Step 3: Final VLSM Summary
# ============================================================

# Subnet | Network        | Prefix | Usable Hosts
# -------|---------------|--------|--------------
# A      | 10.0.0.0       | /13    | 524,286
# B      | 10.8.0.0       | /14    | 262,142
# C      | 10.12.0.0      | /16    | 65,534
# D      | 10.13.0.0      | /18    | 16,382

# ============================================================
# ✅ End of VLSM – Class A Explanation
# ============================================================
```