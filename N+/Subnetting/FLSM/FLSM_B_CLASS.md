
```py
# ============================================================
# 📘 FLSM (Fixed Length Subnet Masking) – Class B Example
# ============================================================

# ----------------------------
# Given Information
# ----------------------------

# Class B address format
# N.N.H.H  → Network.Network.Host.Host

IP = 172.16.0.0/16          # Original Class B network
NEW_PREFIX = /18            # New subnet mask applied (FLSM)

# ----------------------------
# Step 1: Subnet Mask
# ----------------------------

# /18 in binary
# 11111111.11111111.11000000.00000000

SUBNET_MASK = 255.255.192.0 # Decimal subnet mask

# ----------------------------
# Step 2: Subnet Bits
# ----------------------------

# Default Class B mask = /16
# New mask = /18
# Borrowed bits = 18 − 16 = 2 bits

# Binary of borrowed bits (3rd octet)
# 11000000 → 2 subnet bits

# Number of subnets
# 2^SubnetBits = 2^2 = 4 subnets

TOTAL_SUBNETS = 4

# ----------------------------
# Step 3: Host Bits
# ----------------------------

# Total bits = 32
# Host bits = 32 − 18 = 14 bits

# Total IP addresses per subnet
# 2^14 = 16,384 IPs (including Network & Broadcast)

TOTAL_IPS_PER_SUBNET = 16384

# Valid (usable) IPs per subnet
# 2^14 − 2 = 16,382 usable hosts

VALID_HOSTS = 16382

# ----------------------------
# Step 4: Block Size
# ----------------------------

# Block size formula
# 256 − subnet mask value (3rd octet)
# 256 − 192 = 64

BLOCK_SIZE = 64             # Increment in 3rd octet

# ----------------------------
# Step 5: Subnet Table
# ----------------------------

# Subnet 1
# Network   : 172.16.0.0/18
# First IP  : 172.16.0.1
# Last IP   : 172.16.63.254
# Broadcast : 172.16.63.255

# Subnet 2
# Network   : 172.16.64.0/18
# First IP  : 172.16.64.1
# Last IP   : 172.16.127.254
# Broadcast : 172.16.127.255

# Subnet 3
# Network   : 172.16.128.0/18
# First IP  : 172.16.128.1
# Last IP   : 172.16.191.254
# Broadcast : 172.16.191.255

# Subnet 4
# Network   : 172.16.192.0/18
# First IP  : 172.16.192.1
# Last IP   : 172.16.255.254
# Broadcast : 172.16.255.255

# ----------------------------
# Final Summary
# ----------------------------

# Subnet Mask        : 255.255.192.0
# Total Subnets      : 4
# IPs per Subnet     : 16,384
# Valid Hosts        : 16,382
# Block Size         : 64
# Subnetting Octet   : 3rd Octet

# ============================================================
# ✅ End of FLSM – Class B /18 Explanation
# ============================================================
```