# 🌐 Subnetting Cheat Sheet

> A quick reference guide for IPv4 subnetting, CIDR notation, network calculations, and practical examples.

---

## 📖 Table of Contents

- [What is Subnetting?](#-what-is-subnetting)
- [CIDR Notation](#-cidr-notation)
- [Subnet Mask Reference](#-subnet-mask-reference)
- [Usable Hosts](#-usable-hosts)
- [Private IP Address Ranges](#-private-ip-address-ranges)
- [Common Examples](#-common-examples)
- [Quick Binary Reference](#-quick-binary-reference)
- [Useful Commands](#-useful-commands)
- [Administrator Tips](#-administrator-tips)

---

# 📌 What is Subnetting?

Subnetting divides a large network into smaller, manageable networks.

### Benefits

- ✅ Better network organization
- ✅ Improved security
- ✅ Reduced broadcast traffic
- ✅ Efficient IP address allocation

---

# 📘 CIDR Notation

CIDR (Classless Inter-Domain Routing) specifies how many bits belong to the network portion of an IP address.

Example

```text
192.168.10.0/24
```

Meaning

```
24 bits → Network
8 bits  → Hosts
```

---

# 📊 Subnet Mask Reference

| CIDR | Subnet Mask | Hosts | Networks |
|------|-------------|-------:|---------:|
| /30 | 255.255.255.252 | 2 | Point-to-Point |
| /29 | 255.255.255.248 | 6 | Small LAN |
| /28 | 255.255.255.240 | 14 | Small Office |
| /27 | 255.255.255.224 | 30 | Department |
| /26 | 255.255.255.192 | 62 | Medium LAN |
| /25 | 255.255.255.128 | 126 | Large Office |
| /24 | 255.255.255.0 | 254 | Standard LAN |
| /23 | 255.255.254.0 | 510 | Large Network |
| /22 | 255.255.252.0 | 1022 | Campus |
| /21 | 255.255.248.0 | 2046 | Enterprise |
| /20 | 255.255.240.0 | 4094 | Data Center |
| /16 | 255.255.0.0 | 65,534 | Very Large Network |

> [!TIP]
> Usable Hosts = **2^(Host Bits) − 2**

---

# 👥 Usable Hosts

| Host Bits | Hosts |
|-----------:|------:|
| 2 | 2 |
| 3 | 6 |
| 4 | 14 |
| 5 | 30 |
| 6 | 62 |
| 7 | 126 |
| 8 | 254 |
| 9 | 510 |
| 10 | 1022 |

---

# 🏠 Private IP Address Ranges

| Network | CIDR |
|----------|------|
| 10.0.0.0 | /8 |
| 172.16.0.0 – 172.31.255.255 | /12 |
| 192.168.0.0 | /16 |

> [!NOTE]
> Private addresses are **not routable** on the public Internet.

---

# 💡 Common Examples

## Example 1

Network

```
192.168.1.0/24
```

Result

| Item | Value |
|------|-------|
| Network | 192.168.1.0 |
| First Host | 192.168.1.1 |
| Last Host | 192.168.1.254 |
| Broadcast | 192.168.1.255 |

---

## Example 2

```
10.10.20.0/27
```

| Item | Value |
|------|-------|
| Hosts | 30 |
| First | 10.10.20.1 |
| Last | 10.10.20.30 |
| Broadcast | 10.10.20.31 |

---

# 🔢 Quick Binary Reference

| Decimal | Binary |
|---------:|--------|
|128|10000000|
|192|11000000|
|224|11100000|
|240|11110000|
|248|11111000|
|252|11111100|
|254|11111110|
|255|11111111|

---

# 🛠 Useful Commands

| Command | Purpose |
|----------|---------|
| `ip addr` | Display IP configuration |
| `ip route` | View routing table |
| `ping` | Connectivity testing |
| `traceroute` | Path analysis |
| `ipcalc` | Calculate subnet information |

Example

```bash
ipcalc 192.168.1.0/24
```

---

# ⭐ Administrator Tips

> [!TIP]
> Learn `/24`, `/27`, `/28`, `/29`, and `/30` by memory—they're the most common in enterprise environments.

> [!NOTE]
> Always verify:
>
> - Network Address
> - Broadcast Address
> - First Host
> - Last Host
> - Default Gateway

---

## 📚 Quick Cheat Sheet

| CIDR | Hosts |
|------|------:|
| /30 | 2 |
| /29 | 6 |
| /28 | 14 |
| /27 | 30 |
| /26 | 62 |
| /25 | 126 |
| /24 | 254 |
