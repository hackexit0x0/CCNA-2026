```py
# ============================================================
# 📘 FLSM (Fixed Length Subnet Masking) – Class C Example
# ============================================================

# ----------------------------
# Given Information
# ----------------------------

# Class C address format
# N.N.N.H  → Network.Network.Network.Host

IP = 192.168.1.0/24         # Original Class C network
NEW_PREFIX = /26            # New subnet mask applied (FLSM)

# ----------------------------
# Step 1: Subnet Mask
# ----------------------------

# /26 in binary
# 11111111.11111111.11111111.11000000

SUBNET_MASK = 255.255.255.192  # Decimal subnet mask

# ----------------------------
# Step 2: Subnet Bits
# ----------------------------

# Default Class C mask = /24
# New mask = /26
# Borrowed bits = 26 − 24 = 2 bits

# Binary of borrowed bits (4th octet)
# 11000000 → 2 subnet bits

# Number of subnets
# 2^SubnetBits = 2^2 = 4 subnets

TOTAL_SUBNETS = 4

# ----------------------------
# Step 3: Host Bits
# ----------------------------

# Total bits = 32
# Host bits = 32 − 26 = 6 bits

# Total IP addresses per subnet
# 2^6 = 64 IPs (including Network & Broadcast)

TOTAL_IPS_PER_SUBNET = 64

# Valid (usable) IPs per subnet
# 2^6 − 2 = 62 usable hosts

VALID_HOSTS = 62

# ----------------------------
# Step 4: Block Size
# ----------------------------

# Block size formula
# 256 − subnet mask value (4th octet)
# 256 − 192 = 64

BLOCK_SIZE = 64             # Increment in 4th octet

# ----------------------------
# Step 5: Subnet Table
# ----------------------------

# Subnet 1
# Network   : 192.168.1.0/26
# First IP  : 192.168.1.1
# Last IP   : 192.168.1.62
# Broadcast : 192.168.1.63

# Subnet 2
# Network   : 192.168.1.64/26
# First IP  : 192.168.1.65
# Last IP   : 192.168.1.126
# Broadcast : 192.168.1.127

# Subnet 3
# Network   : 192.168.1.128/26
# First IP
```