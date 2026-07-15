# 🌐 Network Troubleshooting Checklist

> **A practical reference handbook for network engineers, system administrators, and IT operations professionals.**

This guide provides a structured methodology for diagnosing and resolving network issues using the **OSI Model**, industry-standard troubleshooting practices, and essential networking tools.

Whether you're investigating a failed SSH connection, DNS resolution problem, high latency, or application outage, this handbook offers a systematic workflow to identify the root cause efficiently.

---

## 📖 Table of Contents

- [Introduction](#-introduction)
- [Troubleshooting Methodology](#-troubleshooting-methodology)
- [OSI Layer 1 – Physical](#-osi-layer-1--physical)
- [OSI Layer 2 – Data Link](#-osi-layer-2--data-link)
- [OSI Layer 3 – Network](#-osi-layer-3--network)
- [OSI Layer 4 – Transport](#-osi-layer-4--transport)
- [OSI Layer 5 – Session](#-osi-layer-5--session)
- [OSI Layer 6 – Presentation](#-osi-layer-6--presentation)
- [OSI Layer 7 – Application](#-osi-layer-7--application)
- [Core Network Commands](#-core-network-commands)
- [Quick Troubleshooting Workflow](#-quick-troubleshooting-workflow)

---

# 📌 Introduction

Modern networks consist of multiple interconnected layers.

Instead of randomly testing commands, experienced engineers troubleshoot from **the bottom up**, verifying each OSI layer before moving to the next.

A structured workflow helps you:

- ✅ Reduce troubleshooting time
- ✅ Identify root causes faster
- ✅ Avoid unnecessary configuration changes
- ✅ Follow a repeatable operational process
- ✅ Improve incident response

> [!TIP]
> **Never assume the issue is DNS.** Start with the physical connection and verify each layer before investigating application-level services.

---

# 🧭 Troubleshooting Methodology

A structured troubleshooting process helps isolate issues quickly and prevents unnecessary changes.

## Step 1 — Identify the Problem

Before running commands, gather information.

### Questions to Ask

- What exactly is failing?
- Is the issue affecting one user or multiple users?
- Did the issue start recently?
- Were any changes made before the failure?
- Can the issue be reproduced?

> [!NOTE]
> A clear problem statement often eliminates unnecessary troubleshooting.

---

## Step 2 — Determine the Scope

Identify whether the issue affects:

| Scope | Example |
|--------|---------|
| 👤 Single User | One workstation cannot reach the server |
| 🏢 Department | Only Finance users are affected |
| 🌍 Entire Site | Office internet outage |
| ☁️ Cloud Service | Azure or AWS service unavailable |

---

## Step 3 — Verify Physical Connectivity

Always begin with the simplest checks.

✔ Cable connected

✔ Link LEDs active

✔ Switch powered on

✔ Wireless signal available

✔ Interface enabled

> [!TIP]
> More network problems are caused by simple physical issues than many engineers expect.

---

## Step 4 — Follow the OSI Model

Always troubleshoot layer by layer.

```text
Physical
     │
     ▼
Data Link
     │
     ▼
Network
     │
     ▼
Transport
     │
     ▼
Session
     │
     ▼
Presentation
     │
     ▼
Application
```

Skipping layers often leads to incorrect conclusions.

---

# 🔌 OSI Layer 1 — Physical

## Purpose

Responsible for transmitting electrical, optical, or wireless signals.

If Layer 1 fails, nothing above it works.

---

## Common Problems

- Damaged Ethernet cable
- Fiber disconnected
- Disabled switch port
- Faulty NIC
- Access Point powered off
- Loose connectors

---

## Checks

| Check | Why |
|--------|-----|
| Cable connected | Verify physical connection |
| LEDs blinking | Confirm link status |
| Network adapter enabled | Interface active |
| Switch powered | Hardware operational |
| Wireless signal | Verify Wi-Fi availability |

---

## Useful Commands

| Command | Description | Use Case |
|----------|-------------|----------|
| `ip link` | Display interface status | Verify interface state |
| `ethtool eth0` | Link speed & duplex | Hardware troubleshooting |
| `nmcli device status` | NetworkManager devices | Desktop troubleshooting |

---

> [!TIP]
> If the interface state is **DOWN**, solve the physical issue before moving to Layer 2.

---

# 🔄 OSI Layer 2 — Data Link

## Purpose

Provides communication between devices on the same local network.

Responsible for:

- MAC Addresses
- Ethernet Frames
- Switching
- VLANs
- ARP

---

## Common Problems

- VLAN mismatch
- Duplicate MAC address
- Incorrect switch port
- STP blocking
- ARP failures

---

## Useful Commands

| Command | Description | Use Case |
|----------|-------------|----------|
| `ip link` | Interface information | Verify interface |
| `arp -a` | Display ARP cache | Check MAC resolution |
| `bridge link` | Linux bridge information | Virtual networking |
| `ip neigh` | Neighbor table | Verify Layer 2 communication |

---

> [!NOTE]
> If devices cannot resolve MAC addresses, communication will never reach Layer 3.

---

# 🌍 OSI Layer 3 — Network

## Purpose

Responsible for logical addressing and routing between networks.

This is where most connectivity problems occur.

---

## Common Problems

- Wrong IP address
- Incorrect subnet mask
- Missing default gateway
- Routing issues
- Firewall blocking traffic

---

## Useful Commands

| Command | Description | Use Case |
|----------|-------------|----------|
| `ip addr` | Show IP configuration | Verify IP address |
| `ip route` | Show routing table | Verify routes |
| `ping` | Test connectivity | Reachability |
| `traceroute` | Display packet path | Routing analysis |

---

### Example

```bash
ip addr
ip route
ping 8.8.8.8
```

---

> [!TIP]
> If `ping` to the gateway fails, the issue is usually local (Layer 1–3).

---

# 🚪 OSI Layer 4 — Transport

## Purpose

Manages communication using TCP and UDP.

Responsible for:

- Port numbers
- Reliable delivery
- Sessions
- TCP handshakes

---

## Common Problems

- Closed ports
- Firewall rules
- Service not listening
- TCP timeout

---

## Useful Commands

| Command | Description | Use Case |
|----------|-------------|----------|
| `ss -tulnp` | Display listening ports | Verify services |
| `nc` | Test TCP/UDP ports | Connectivity testing |
| `telnet host port` | Test open ports | Legacy diagnostics |

---

> [!TIP]
> If the service isn't listening on the expected port, investigate the application before the network.

---

# 🔐 OSI Layer 5 — Session

## Purpose

Establishes, maintains, and terminates communication sessions.

Examples include:

- SSH
- SMB
- RPC

Typical issues involve dropped sessions, expired authentication, or interrupted connections.

---

# 🔒 OSI Layer 6 — Presentation

## Purpose

Responsible for data formatting, encryption, and compression.

Common examples include:

- SSL/TLS certificates
- HTTPS encryption
- Character encoding

---

## Common Problems

- Expired certificates
- TLS version mismatch
- Certificate trust errors

---

# 🌐 OSI Layer 7 — Application

## Purpose

The layer users interact with directly.

Examples:

- HTTP
- HTTPS
- DNS
- FTP
- SMTP
- SSH

---

## Useful Commands

| Command | Description | Use Case |
|----------|-------------|----------|
| `curl` | Test HTTP/HTTPS | Verify web services |
| `wget` | Download content | Connectivity validation |
| `dig` | DNS lookup | DNS troubleshooting |
| `nslookup` | Name resolution | Verify DNS records |
| `host` | DNS queries | Quick DNS testing |

---

### Example

```bash
curl -I https://example.com
```

---

> [!TIP]
> If DNS fails but pinging an IP address works, investigate your DNS configuration before checking the web server.

---

# 📚 Core Network Commands

| Command | Description | Typical Use |
|----------|-------------|-------------|
| `ip addr` | Show IP configuration | Verify addresses |
| `ip route` | Show routing table | Routing issues |
| `ping` | Connectivity test | Reachability |
| `traceroute` | Path analysis | Routing |
| `ss -tulnp` | Listening ports | Service verification |
| `curl` | HTTP requests | Web diagnostics |
| `dig` | DNS lookup | DNS troubleshooting |
| `tcpdump` | Capture packets | Deep network analysis |
| `arp -a` | ARP cache | Layer 2 verification |
| `ip neigh` | Neighbor table | MAC resolution |

---

# 🚀 Quick Troubleshooting Workflow

```text
🚨 Network Issue
      │
      ▼
🔌 Check cables & interface
      │
      ▼
📡 Verify IP configuration
      │
      ▼
🌍 Ping gateway
      │
      ▼
🛣 Verify routing
      │
      ▼
🌐 Test DNS resolution
      │
      ▼
🚪 Verify open ports
      │
      ▼
🌍 Test application
      │
      ▼
📦 Capture packets (if needed)
      │
      ▼
✅ Identify Root Cause
```

---
