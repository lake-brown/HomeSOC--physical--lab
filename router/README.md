# Router Security

## Overview

The router is the primary security boundary for the HomeSOC-Lab environment.

The lab uses a dedicated **GL-SFT1200 Opal** router positioned behind the home router. This creates a separate lab network where security controls can be configured and validated without exposing the home network to lab experimentation.

### Network Architecture

```text
                    Internet
                       │
                       ▼
                ┌──────────────┐
                │ Home Router  │
                │   Internet   │
                └──────┬───────┘
                       │
                       ▼
                ┌──────────────┐
                │ GL-SFT1200   │
                │ Opal Router  │
                │              │
                │ Firewall/NAT │
                └──────┬───────┘
                       │
                 Private Lab LAN
                       │
              ┌────────┴────────┐
              │                 │
              ▼                 ▼
       Ubuntu Lenovo       Raspberry Pi
        Workstation         Ubuntu Server
```

### Security Objectives

The router configuration is designed to provide:

- Network isolation from the home network
- Controlled Internet access for lab systems
- Secure wireless access
- Stateful firewall protection
- NAT between the lab and upstream network
- No unnecessary inbound exposure
- A controlled environment for cybersecurity testing
- A foundation for Wazuh, Suricata, Splunk, and Wireshark projects

---

# Router Security Projects

| Project                                                     | Status      | Focus                                        |
| ----------------------------------------------------------- | ----------- | -------------------------------------------- |
| [Project 1 — Wireless Security](wireless-security.md)       | ✅ Complete | Secure lab wireless network                  |
| [Project 2 — Firewall & Network Segmentation](firewall.md)  | ✅ Complete | Firewall configuration and network isolation |
| [Project 3 — Firmware Security](firmware.md)                | ⏳ Planned  | Router firmware updates and security         |
| [Project 4 — Configuration Backup](configuration-backup.md) | ⏳ Planned  | Secure router configuration backup           |
| [Project 5 — Security Validation](security-validation.md)   | ⏳ Planned  | Validate router security controls            |

---

# Project 1 — Wireless Security

**Objective:** Create a dedicated and secured wireless network for the cybersecurity lab.

### Controls

- Dedicated lab SSID
- WPA2/WPA3 wireless security
- Strong unique wireless password
- 2.4 GHz support for Raspberry Pi connectivity
- WPS disabled where available
- Lab devices connected separately from the home wireless network

### Result

The lab wireless network provides connectivity for authorized lab systems while keeping the cybersecurity environment separate from the normal home wireless network.

[View Project 1 Documentation →](wireless-security.md)

---

# Project 2 — Firewall & Network Segmentation

**Objective:** Configure and validate the router's security boundary between the lab network, upstream home network, and Internet.

## Intended Traffic Policy

| Traffic            | Policy   |
| ------------------ | -------- |
| Lab → Internet     | ✅ Allow |
| Lab → Home Network | 🚫 Block |
| Home Network → Lab | 🚫 Block |
| Internet → Lab     | 🚫 Block |
| Lab → Lab          | ✅ Allow |

## Firewall Baseline

The following inbound exposure controls were reviewed:

```text
Port forwarding:        None configured
Manually opened ports:  None configured
DMZ:                    Disabled
Unnecessary services:   Not exposed
Firewall:               Enabled
NAT:                    Enabled
```

No TCP or UDP ports were intentionally opened for inbound access to the lab.

## Network Segmentation Rule

A firewall rule was configured on the Opal to prevent lab devices from reaching private RFC1918 address ranges through the WAN interface.

```text
Source Zone:       LAN
Destination Zone:  WAN

Destination:
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16

Action:
DROP
```

### Purpose

The rule prevents HomeSOC lab devices from initiating connections to private networks reachable through the Opal WAN interface.

This provides an additional security boundary between the cybersecurity lab and devices located on the upstream Internet Provider network.

Public Internet connectivity remains available.

---

## Validation

Testing was performed from the Ubuntu Lenovo workstation connected to the Opal lab network.

### Gateway Verification

The workstation was verified to use the Opal as its default gateway.

```bash
ip route
```

The lab workstation uses the Opal LAN interface as its default route.

### Internet Connectivity

External connectivity was verified using a public IP address:

```bash
ping -c 4 8.8.8.8
```

**Result:** ✅ Internet connectivity maintained.

DNS connectivity was also tested:

```bash
ping -c 4 google.com
```

**Result:** ✅ External connectivity maintained.

### Upstream Gateway

The Internet Provider upstream gateway remained reachable from the lab.

**Result:** ⚠️ Gateway reachable.

This behavior does not by itself indicate that the lab has unrestricted access to the upstream network. The upstream gateway is the next-hop router used by the Opal WAN interface.

### Upstream Host Isolation

A device connected to the Internet Provider network was tested from the HomeSOC lab.

The lab workstation could not reach the tested Internet Provider-side device.

**Result:** 🚫 Upstream host-to-host connectivity blocked.

This confirms that the configured RFC1918 filtering rule is preventing the lab from reaching other private hosts on the upstream network.

---

## Security Validation Results

| Test                              | Result       |
| --------------------------------- | ------------ |
| Lab uses Opal as gateway          | ✅ Pass      |
| Lab → Internet                    | ✅ Pass      |
| Lab → Internet Provider gateway   | ⚠️ Reachable |
| Lab → Internet Provider-side host | 🚫 Blocked   |
| WAN → Lab unsolicited access      | 🚫 Blocked   |
| Unnecessary port forwarding       | ✅ None      |
| DMZ                               | ✅ Disabled  |
| Unnecessary inbound ports         | ✅ None      |

### Current Finding

The HomeSOC lab is successfully separated from other hosts on the upstream Internet Provider network while maintaining Internet connectivity.

The upstream gateway remains reachable because it serves as the Opal's next-hop gateway. This is documented as an expected behavior rather than treating gateway reachability alone as evidence of failed segmentation.

---

# Project 3 — Firmware Security

**Objective:** Ensure the router is running current firmware and document the update process.

### Planned Activities

- Identify current firmware version
- Check for available updates
- Apply firmware update if required
- Verify router functionality after the update
- Document the final firmware version
- Record the update date

[View Project 3 Documentation →](firmware.md)

---

# Project 4 — Configuration Backup

**Objective:** Create a secure backup of the router configuration.

### Planned Activities

- Export router configuration
- Verify backup availability
- Store backup securely
- Ensure sensitive configuration data is not committed to GitHub
- Document the restoration process

> **Security Note:** Router configuration backups may contain sensitive information and must not be uploaded to the public repository.

[View Project 4 Documentation →](configuration-backup.md)

---

# Project 5 — Security Validation

**Objective:** Perform a final security review of the router and verify that the intended security controls are functioning.

### Planned Validation

- Wireless security
- Firewall configuration
- Port forwarding
- Open ports
- DMZ configuration
- Network isolation
- Internet connectivity
- Upstream network access
- Administrative access
- Firmware status

Results will be documented as part of the final HomeSOC-Lab security assessment.

[View Project 5 Documentation →](security-validation.md)

---

# Security & Privacy

This repository intentionally excludes sensitive network information.

### Do Not Commit

- Public IP addresses
- Home network addresses
- Wi-Fi passwords
- Router administrator passwords
- SSH credentials
- API keys
- Private keys
- MAC addresses
- Device serial numbers
- Configuration backups containing credentials
- Personal information

Use generalized or sanitized values in screenshots and documentation.

---

# Tools Used

- GL-SFT1200 Opal
- Ubuntu Linux
- Nmap
- Wireshark
- Git
- GitHub

---

# Project Status

**Router Security Phase:** 🚧 In Progress

**Firewall & Network Segmentation:** ✅ Complete

The router security phase establishes the network foundation for the remainder of the HomeSOC-Lab.

Future work will build on this foundation with:

- Raspberry Pi endpoint hardening
- Network reconnaissance
- Wireshark traffic investigation
- Wazuh endpoint monitoring
- Suricata network detection
- Splunk SIEM analysis
- SOC investigation workflows
