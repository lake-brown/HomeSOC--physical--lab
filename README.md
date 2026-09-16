# HomeSOC-Lab

> **Status:** 🚧 In Progress

> A hands-on cybersecurity homelab for practicing network segmentation, Linux administration, centralized logging, security monitoring, detection engineering, and incident response.

## Overview

HomeSOC-Lab is a small, isolated security lab built with physical networking and Linux systems. The goal is to create a realistic environment where I can deploy systems, collect security telemetry, investigate events, and document the process like a SOC analyst.

This project is being built incrementally, with each phase documented as it is completed.

## Lab Architecture

```text
                              Internet

                                 │

                                 ▼

                       ┌──────────────────┐
                       │ Internet / Home  │
                       │     Gateway      │
                       │                  │
                       │   Main Network   │
                       └────────┬─────────┘
                                │
                                │ WAN
                                ▼
                       ┌──────────────────┐
                       │  Dedicated Lab   │
                       │      Router      │
                       │                  │
                       │ Firewall / NAT   │
                       │  DHCP / Wi-Fi    │
                       └────────┬─────────┘
                                │
                         Private Lab LAN
                                │
                    ┌───────────┴───────────┐
                    │                       │
                    ▼                       ▼
            ┌─────────────────┐     ┌──────────────────┐
            │  Raspberry Pi   │     │     Lenovo       │
            │  Ubuntu Server  │     │ Ubuntu Desktop   │
            │                 │     │                  │
            │ Linux Server /  │     │ SOC Workstation  │
            │ Lab Endpoint    │     │                  │
            └─────────────────┘     └──────────────────┘
```

> **Privacy note:** Real IP addresses, Wi-Fi credentials, passwords, MAC addresses, and other sensitive network information are intentionally excluded from this repository. Examples use placeholders or documentation-only values.

## Hardware

| Device                  | Role                                                     |
| ----------------------- | -------------------------------------------------------- |
| Dedicated Lab Router    | Lab firewall, NAT gateway, DHCP, and wireless networking |
| Raspberry Pi 3A         | Linux server / monitored endpoint                        |
| Lenovo IdeaPad          | Ubuntu security workstation                              |
| Internet / Home Gateway | Upstream Internet connection and home network            |

## Technology Stack

### Network Infrastructure

- Dedicated Lab Router
- Firewall
- NAT
- DHCP
- Wireless networking
- Network segmentation
- SSH
- TCP/IP

### Operating Systems

- Ubuntu Server
- Ubuntu Desktop
- Raspberry Pi

### Security Monitoring

- Splunk
- Wazuh
- Suricata
- Zeek
- Wireshark
- Security Onion

### Development & Documentation

- Python
- Bash
- Git
- GitHub
- Markdown

> Tools are added to the project as they are actually deployed, configured, and tested.

## Project Goals

- Build an isolated physical cybersecurity lab
- Design and document a secure network architecture
- Configure a dedicated lab router
- Practice firewall and NAT configuration
- Implement network segmentation
- Deploy and administer a Linux server
- Practice Linux system hardening
- Configure secure remote administration with SSH
- Establish centralized logging infrastructure
- Deploy security monitoring tools
- Deploy a SIEM
- Collect and monitor security telemetry
- Build a foundation for detection engineering
- Validate security controls through controlled testing
- Document configurations, troubleshooting, and lessons learned

## Project Phases

### Phase 1 — Network Infrastructure

**Focus:** Build and secure the isolated lab network.

- [x] Configure dedicated lab router
- [x] Establish private lab LAN
- [x] Configure lab wireless network
- [x] Review wireless security
- [x] Configure/review firewall rules
- [x] Verify NAT configuration
- [x] Verify DHCP configuration
- [x] Update router firmware if required
- [x] Create router configuration backup
- [x] Test network segmentation
- [x] Document network architecture

### Phase 2 — Linux Infrastructure & Hardening

**Focus:** Deploy and secure the Raspberry Pi Ubuntu Server.

- [x] Install Ubuntu Server
- [x] Connect Raspberry Pi to lab network
- [ ] Configure hostname
- [ ] Configure SSH
- [ ] Verify administrative access
- [ ] Create/verify administrative accounts
- [ ] Apply system updates
- [ ] Configure file and directory permissions
- [ ] Configure host firewall
- [ ] Harden SSH
- [ ] Review listening services and ports
- [ ] Configure system logging
- [ ] Document Linux security baseline

### Phase 3 — Security Monitoring Infrastructure

**Focus:** Establish endpoint and network security monitoring.

- [ ] Define security telemetry requirements
- [ ] Document logging architecture
- [ ] Deploy Wazuh
- [ ] Configure endpoint monitoring
- [ ] Deploy Suricata
- [ ] Configure network monitoring
- [ ] Verify security event collection
- [ ] Review endpoint and network alerts
- [ ] Document monitoring architecture
- [ ] Validate telemetry visibility

### Phase 4 — SIEM & SOC Integration

**Focus:** Centralize security telemetry and build the SOC monitoring layer.

- [ ] Deploy Splunk
- [ ] Configure data inputs
- [ ] Forward Raspberry Pi logs
- [ ] Integrate relevant security telemetry
- [ ] Verify log ingestion
- [ ] Create security searches
- [ ] Create dashboards
- [ ] Configure initial alerts
- [ ] Validate Wazuh/Splunk integration
- [ ] Validate Suricata/Splunk integration
- [ ] Document end-to-end data flow

### Phase 5 — Validation, Documentation & Assessment

**Focus:** Validate the completed infrastructure and document the finished SOC environment.

- [ ] Perform network security validation
- [ ] Verify firewall and segmentation behavior
- [ ] Validate Linux hardening
- [ ] Validate SSH security
- [ ] Verify endpoint telemetry
- [ ] Verify network telemetry
- [ ] Verify SIEM ingestion
- [ ] Test security event visibility
- [ ] Finalize architecture diagrams
- [ ] Review and redact screenshots
- [ ] Document troubleshooting
- [ ] Document lessons learned
- [ ] Complete final lab assessment
- [ ] Review and organize GitHub repository

## Infrastructure Progression

```text
Phase 1
Network Infrastructure
        │
        ▼
Phase 2
Linux Infrastructure & Hardening
        │
        ▼
Phase 3
Security Monitoring Infrastructure
        │
        ▼
Phase 4
SIEM & SOC Integration
        │
        ▼
Phase 5
Validation, Documentation & Assessment
```

## Network Security Approach

The lab is designed as a separate network behind the existing home gateway.

```text
Home Network
     │
     ▼
Dedicated Lab Router
     │
     ▼
Private Lab Network
     │
     ├── Raspberry Pi
     │
     └── Ubuntu Workstation
```

The objective is to prevent unnecessary direct exposure of lab systems to the normal home network while allowing the lab to access the Internet when required.

Firewall behavior and segmentation will be tested and documented rather than assumed.

## Security & Privacy

This repository intentionally does **not** contain:

- Real public IP addresses
- Real home-network IP addresses
- Wi-Fi passwords
- SSH passwords
- API keys
- Private keys
- MAC addresses
- Authentication tokens
- Personal network identifiers

When screenshots are added, sensitive information will be redacted before publication.

Example documentation:

```text
LAB_ROUTER_IP=<LAB_ROUTER_IP>

SERVER_IP=<SERVER_IP>

WORKSTATION_IP=<WORKSTATION_IP>

HOME_GATEWAY_IP=<HOME_GATEWAY_IP>
```

## Lessons Learned

This section will document:

- Network configuration problems
- Linux configuration problems
- Troubleshooting steps
- Firewall behavior
- Access control decisions
- Monitoring challenges
- Detection tuning
- False positives
- Investigation findings
- Security improvements

## Skills Demonstrated

### Networking

- Network segmentation
- TCP/IP
- DHCP
- NAT
- Firewall configuration
- Wireless security
- Network troubleshooting
- Network reconnaissance

### Linux

- Ubuntu Server administration
- SSH
- Users and groups
- File permissions
- ACLs
- UFW
- System services
- System logging
- Linux hardening

### Security Operations

- SIEM
- Log analysis
- Alert triage
- Endpoint monitoring
- Network security monitoring
- IDS
- Detection engineering
- Threat investigation
- Incident response

### Security Tools

- Splunk
- Wazuh
- Suricata
- Wireshark
- Nmap

### Documentation

- Technical documentation
- Security reports
- Investigation reports
- Git
- GitHub
- Markdown

## Project Status

**Current focus:** Building the lab network and Raspberry Pi Linux server.

Future updates will document the deployment, configuration, detections, investigations, and lessons learned as the lab develops.
