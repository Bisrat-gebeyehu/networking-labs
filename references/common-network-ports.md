# 🚪 Common Network Ports Reference

> A practical reference guide to common TCP and UDP ports used in networking, Linux administration, and infrastructure troubleshooting.

---

## 📖 Table of Contents

- [Well-Known Ports](#-well-known-ports)
- [Web Services](#-web-services)
- [Remote Access](#-remote-access)
- [DNS & DHCP](#-dns--dhcp)
- [Email Services](#-email-services)
- [File Sharing](#-file-sharing)
- [Monitoring & Logging](#-monitoring--logging)
- [Databases](#-databases)
- [Useful Commands](#-useful-commands)
- [Administrator Tips](#-administrator-tips)

---

# 🌍 Well-Known Ports

| Port | Protocol | Service | Typical Use |
|------:|:--------:|---------|-------------|
|20|TCP|FTP Data|File transfer|
|21|TCP|FTP|File transfer|
|22|TCP|SSH|Remote administration|
|23|TCP|Telnet|Legacy remote access|
|25|TCP|SMTP|Mail transfer|
|53|TCP/UDP|DNS|Name resolution|
|67|UDP|DHCP Server|IP assignment|
|68|UDP|DHCP Client|Receive IP|
|69|UDP|TFTP|Network boot|
|80|TCP|HTTP|Web traffic|
|110|TCP|POP3|Email retrieval|
|123|UDP|NTP|Time synchronization|
|143|TCP|IMAP|Email retrieval|
|161|UDP|SNMP|Monitoring|
|162|UDP|SNMP Trap|Alerts|
|179|TCP|BGP|Routing|
|389|TCP|LDAP|Directory services|
|443|TCP|HTTPS|Secure web|
|445|TCP|SMB|Windows file sharing|
|514|UDP|Syslog|Logging|
|636|TCP|LDAPS|Secure LDAP|

---

# 🌐 Web Services

| Port | Service |
|------|---------|
|80|HTTP|
|443|HTTPS|
|8080|Alternative HTTP|
|8443|Alternative HTTPS|

---

# 🔐 Remote Access

| Port | Service |
|------|---------|
|22|SSH|
|23|Telnet|
|3389|Remote Desktop (RDP)|
|5900|VNC|

> [!TIP]
> Disable Telnet whenever possible and use SSH instead.

---

# 🌍 DNS & DHCP

| Port | Service |
|------|---------|
|53 TCP|Zone Transfers|
|53 UDP|DNS Queries|
|67 UDP|DHCP Server|
|68 UDP|DHCP Client|

---

# 📧 Email Services

| Port | Service |
|------|---------|
|25|SMTP|
|110|POP3|
|143|IMAP|
|465|SMTPS|
|587|SMTP Submission|
|993|IMAPS|
|995|POP3S|

---

# 📂 File Sharing

| Port | Service |
|------|---------|
|20|FTP Data|
|21|FTP|
|22|SFTP|
|69|TFTP|
|445|SMB|
|2049|NFS|

---

# 📊 Monitoring & Logging

| Port | Service |
|------|---------|
|161|SNMP|
|162|SNMP Trap|
|514|Syslog|
|9090|Prometheus|
|3000|Grafana|

---

# 🗄 Databases

| Port | Database |
|------|----------|
|1433|Microsoft SQL Server|
|1521|Oracle|
|3306|MySQL|
|5432|PostgreSQL|
|6379|Redis|
|27017|MongoDB|

---

# 🛠 Useful Commands

### Show Listening Ports

```bash
ss -tulnp
```

### Test a Port

```bash
nc -zv 192.168.1.10 443
```

### Scan with Nmap

```bash
nmap -Pn 192.168.1.10
```

### Test HTTPS

```bash
curl -I https://example.com
```

### Check DNS

```bash
dig example.com
```

---

# ⭐ Administrator Tips

> [!TIP]
> If a service is unreachable:
>
> 1. Verify the service is running.
> 2. Confirm the port is listening (`ss -tulnp`).
> 3. Check firewall rules.
> 4. Test connectivity (`nc`, `telnet`, or `nmap`).
> 5. Review service logs.

> [!WARNING]
> Open only the ports your application requires. Unnecessary open ports increase the attack surface.

---

## 🚀 Quick Reference

| Service | Port |
|---------|------|
|SSH|22|
|DNS|53|
|HTTP|80|
|HTTPS|443|
|SMB|445|
|RDP|3389|
|MySQL|3306|
|PostgreSQL|5432|
|Redis|6379|
|Grafana|3000|
|Prometheus|9090|
