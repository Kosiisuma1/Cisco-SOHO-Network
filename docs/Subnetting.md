# IPv4 Subnetting Design

## Project Overview

The objective of this project was to design a subnetting scheme for a Small Office/Home Office (SOHO) network supporting three separate departments.

The company was allocated the following network by the ISP:

```
Base Network: 192.168.1.0/24
```

The network needed to support:

- Admin / IT
- Finance / HR
- Customer Service / Reception

Each department required its own subnet and VLAN while maintaining communication through Inter-VLAN Routing.

---

# Step 1 – Determine Number of Required Subnets

Departments:

- Admin / IT
- Finance / HR
- Customer Service

Total required subnets:

```
3
```

Using the subnet formula:

```
2ⁿ ≥ Required Subnets
```

```
2² = 4
```

Borrowing **2 bits** provides **4 available subnets**, which satisfies the requirement.

---

# Step 2 – Calculate the New Subnet Mask

Original network:

```
192.168.1.0/24
```

Original Mask

```
255.255.255.0
```

Borrowed Bits

```
2
```

New Prefix

```
/26
```

New Subnet Mask

```
255.255.255.192
```

Binary Representation

```
11111111.11111111.11111111.11000000
```

---

# Step 3 – Calculate the Block Size

The interesting octet is:

```
192
```

Block Size Formula

```
256 - 192 = 64
```

Block Size

```
64
```

Subnet ranges therefore increment by 64.

```
0
64
128
192
```

---

# VLAN 10 – Admin / IT

| Item | Value |
|------|------|
| Network Address | 192.168.1.0/26 |
| Default Gateway | 192.168.1.1 |
| First Usable Host | 192.168.1.1 |
| Last Usable Host | 192.168.1.62 |
| Broadcast Address | 192.168.1.63 |

---

# VLAN 20 – Finance / HR

| Item | Value |
|------|------|
| Network Address | 192.168.1.64/26 |
| Default Gateway | 192.168.1.65 |
| First Usable Host | 192.168.1.65 |
| Last Usable Host | 192.168.1.126 |
| Broadcast Address | 192.168.1.127 |

---

# VLAN 30 – Customer Service / Reception

| Item | Value |
|------|------|
| Network Address | 192.168.1.128/26 |
| Default Gateway | 192.168.1.129 |
| First Usable Host | 192.168.1.129 |
| Last Usable Host | 192.168.1.190 |
| Broadcast Address | 192.168.1.191 |

---

# Unused Subnet

The remaining subnet was reserved for future expansion.

| Network | Range |
|---------|------|
| 192.168.1.192/26 | Reserved |

---

# VLAN Assignment

| VLAN | Department | Network |
|------|------------|----------------|
| 10 | Admin / IT | 192.168.1.0/26 |
| 20 | Finance / HR | 192.168.1.64/26 |
| 30 | Customer Service / Reception | 192.168.1.128/26 |

---

# Design Considerations

The subnetting scheme was designed to:

- Separate departments into isolated broadcast domains.
- Reduce unnecessary broadcast traffic.
- Improve network security through VLAN segmentation.
- Allow routing between departments using Router-on-a-Stick.
- Support automatic IP address allocation using DHCP.
- Leave one additional subnet available for future business growth.

---

# Key Networking Concepts Demonstrated

- IPv4 Addressing
- Subnetting
- CIDR Notation
- Network ID Calculation
- Broadcast Address Calculation
- Default Gateway Planning
- VLAN Segmentation
- Router-on-a-Stick
- DHCP Address Planning
- Enterprise Network Design

---

## Outcome

The subnetting plan successfully supports all three business departments while providing room for future expansion. Each VLAN operates within its own IP subnet, and devices communicate across departments through Inter-VLAN Routing configured on the Cisco router.
