```py
# ============================================================
# 📘 FLSM (Fixed Length Subnet Masking) – Class A Example
# ============================================================

# ----------------------------
# Given Information
# ----------------------------

# Class A address format
# N.H.H.H  → Network.Host.Host.Host

IP = 10.0.0.0/8             # Original Class A network
NEW_PREFIX = /12            # New subnet mask applied (FLSM)

# ----------------------------
# Step 1: Subnet Mask
# ----------------------------

# /12 in binary
# 11111111.11110000.00000000.00000000

SUBNET_MASK = 255.240.0.0   # Decimal subnet mask

# ----------------------------
# Step 2: Subnet Bits
# ----------------------------

# Default Class A mask = /8
# New mask = /12
# Borrowed bits = 12 − 8 = 4 bits

# Binary of borrowed bits (in 2nd octet)
# 11110000 → 4 bits used for subnetting

# Number of subnets
# 2^SubnetBits = 2^4 = 16 subnets

TOTAL_SUBNETS = 16

# ----------------------------
# Step 3: Host Bits
# ----------------------------

# Total bits = 32
# Host bits = 32 − 12 = 20 bits

# Total IP addresses per subnet
# 2^20 = 1,048,576 IPs (including Network & Broadcast)

TOTAL_IPS_PER_SUBNET = 1048576

# Valid (usable) IPs per subnet
# 2^20 − 2 = 1,048,574 usable hosts

VALID_HOSTS = 1048574

# ----------------------------
# Step 4: Block Size
# ----------------------------

# Block size formula
# 256 − subnet mask value (2nd octet)
# 256 − 240 = 16

BLOCK_SIZE = 16             # Increment in 2nd octet

# ----------------------------
# Step 5: Subnet Table
# ----------------------------

# Subnet 1
# Network   : 10.0.0.0/12
# First IP  : 10.0.0.1
# Last IP   : 10.15.255.254
# Broadcast : 10.15.255.255

# Subnet 2
# Network   : 10.16.0.0/12
# First IP  : 10.16.0.1
# Last IP   : 10.31.255.254
# Broadcast : 10.31.255.255

# Subnet 3
# Network   : 10.32.0.0/12
# First IP  : 10.32.0.1
# Last IP   : 10.47.255.254
# Broadcast : 10.47.255.255

# Subnet 4
# Network   : 10.48.0.0/12
# First IP  : 10.48.0.1
# Last IP   : 10.63.255.254
# Broadcast : 10.63.255.255

# ...
# (Same pattern continues up to 16 subnets)

# ----------------------------
# Final Summary
# ----------------------------

# Subnet Mask        : 255.240.0.0
# Total Subnets      : 16
# IPs per Subnet     : 1,048,576
# Valid Hosts        : 1,048,574
# Block Size         : 16
# Subnetting Octet   : 2nd Octet

# ============================================================
# ✅ End of FLSM – Class A /12 Explanation
# ============================================================
```