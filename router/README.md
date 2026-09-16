# Router Security

**Status:** Complete

The **Router Security** project establishes the network security foundation for the HomeSOC-Lab.

A dedicated **Firewall Router** is positioned behind the existing home router to create an isolated lab network. The environment provides controlled Internet access while restricting unnecessary communication between the cybersecurity lab and the home network.

---

## Network Architecture

```text
Internet
   │
   ▼
Home Router
   │
   ▼
Firewall Router
Firewall / NAT / DHCP / Wi-Fi
   │
   ▼
Private Lab Network
   │
   ├── Ubuntu Workstation
   │
   └── Raspberry Pi
          Ubuntu Server
```

The Firewall Router acts as the primary security boundary for the lab environment.

---

## Security Objectives

The router security project focuses on:

- Network segmentation
- Firewall configuration
- Secure wireless access
- Controlled Internet connectivity
- NAT
- Minimizing inbound exposure
- Firmware security
- Configuration recovery
- Security validation
- Network security testing

---

# Router Security Projects

| Project                                                     | Status      | Focus                                        |
| ----------------------------------------------------------- | ----------- | -------------------------------------------- |
| [Project 1 — Wireless Security](wireless-security.md)       | ✅ Complete | Secure lab wireless network                  |
| [Project 2 — Firewall & Network Segmentation](firewall.md)  | ✅ Complete | Firewall configuration and network isolation |
| [Project 3 — Firmware Security](firmware.md)                | ✅ Complete | Firmware security and updates                |
| [Project 4 — Configuration Backup](configuration-backup.md) | ✅ Complete | Secure configuration backup                  |
| [Project 5 — Security Validation](security-validation.md)   | ✅ Complete | Validate router security controls            |

---

# Project 1 — Wireless Security

**Status:** ✅ Complete

Established a dedicated and secured wireless network for the cybersecurity lab.

Key areas:

- Wireless security
- Dedicated lab SSID
- Secure authentication
- Raspberry Pi connectivity
- Separation from home wireless

[View Project 1 Documentation →](wireless-security.md)

---

# Project 2 — Firewall & Network Segmentation

**Status:** ✅ Complete

Configured the Firewall Router to establish a security boundary between the private lab network and the upstream home network.

Key areas:

- Firewall rules
- Network segmentation
- NAT
- Internet access
- Upstream network isolation
- Inbound exposure controls

[View Project 2 Documentation →](firewall.md)

---

# Project 3 — Firmware Security

**Status:** ✅ Complete

Reviewed and updated the Firewall Router firmware and verified normal router functionality following the update.

Key areas:

- Firmware review
- Firmware updates
- Post-update verification
- Router security review

[View Project 3 Documentation →](firmware.md)

---

# Project 4 — Configuration Backup

**Status:** ✅ Complete

Created and securely stored a router configuration backup for recovery purposes.

Key areas:

- Configuration archive generation
- Backup storage
- Recovery planning
- Sensitive configuration protection

Router configuration backups are intentionally excluded from GitHub.

[View Project 4 Documentation →](configuration-backup.md)

---

# Project 5 — Security Validation

**Status:** ✅ Complete

Performed security validation of the router configuration and segmentation controls.

Key areas:

- Nmap scanning
- Firewall validation
- Network isolation testing
- Internet connectivity testing
- Inbound exposure review
- Port forwarding review
- DMZ review
- Administrative access review

Testing confirmed that the lab maintained Internet connectivity while access to tested hosts on the upstream private network was restricted.

[View Project 5 Documentation →](security-validation.md)

---

# Security Controls

The completed router security phase established the following controls:

```text
Firewall                  Enabled
NAT                       Enabled
Network Segmentation      Enabled
Lab Internet Access       Enabled
Port Forwarding           None
DMZ                       Disabled
Unnecessary Inbound Ports None
Configuration Backup      Created
Security Validation       Completed
```

---

# Validation Approach

The router was validated using configuration review and controlled testing.

Tools and techniques included:

- Nmap
- Connectivity testing
- Firewall rule review
- Network segmentation testing
- Service discovery
- Inbound exposure review

The purpose of validation was to verify that configured security controls behaved as intended.

Detailed testing results are documented in:

[Project 5 — Security Validation](security-validation.md)

---

# Repository Structure

```text
router/
├── README.md
├── wireless-security.md
├── firewall.md
├── firmware.md
├── configuration-backup.md
└── security-validation.md
```

The main README provides the project overview.

Each project document contains the detailed configuration, methodology, testing, results, and lessons learned for that specific project.

---

# Security & Privacy

This repository intentionally excludes sensitive network information.

### Do Not Commit

- IP addresses
- Home network addresses
- Wi-Fi passwords
- Router administrator passwords
- SSH credentials
- API keys
- Private keys
- MAC addresses
- Device serial numbers
- Configuration backups containing sensitive information
- Personal information

Use generalized or sanitized values in documentation and screenshots.

---

# Tools Used

- Firewall Router
- LuCI
- Ubuntu Linux
- Nmap
- Wireshark
- Git
- GitHub

---

# Project Status

**Router Security Phase:** ✅ Complete

All five router security projects have been completed:

```text
Wireless Security
       │
       ▼
Firewall & Segmentation
       │
       ▼
Firmware Security
       │
       ▼
Configuration Backup
       │
       ▼
Security Validation
       │
       ▼
   ✅ COMPLETE
```

The completed router security phase provides the network foundation for the next stage of the HomeSOC-Lab:

- Raspberry Pi endpoint hardening
- Linux security configuration
- Network reconnaissance
- Wireshark traffic investigation
- Wazuh endpoint monitoring
- Suricata network detection
- Splunk SIEM analysis
- SOC investigation workflows
