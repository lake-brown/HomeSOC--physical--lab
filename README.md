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
                    ┌─────────────────┐
                    │  Home Gateway   │
                    │  Main Network   │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  GL-SFT1200     │
                    │  Lab Router     │
                    │  Firewall / NAT │
                    └────────┬────────┘
                             │
                       Private Lab LAN
                             │
                  ┌──────────┴──────────┐
                  │                     │
                  ▼                     ▼
          ┌───────────────┐     ┌────────────────┐
          │ Raspberry Pi  │     │ Lenovo IdeaPad │
          │ Ubuntu Server │     │ Ubuntu         │
          │               │     │ SOC Workstation│
          └───────────────┘     └────────────────┘
```

> **Privacy note:** Real IP addresses, Wi-Fi credentials, passwords, MAC addresses, and other sensitive network information are intentionally excluded from this repository. Examples use placeholders or documentation-only values.

## Hardware

| Device          | Role                                            |
| --------------- | ----------------------------------------------- |
| GL-SFT1200      | Dedicated lab router, firewall, and NAT gateway |
| Raspberry Pi 3A | Linux server / monitored endpoint               |
| Lenovo IdeaPad  | Ubuntu security workstation                     |

## Technology Stack

Current and planned technologies:

- Ubuntu Server
- Ubuntu Desktop
- Raspberry Pi
- GL-SFT1200
- SSH
- Splunk
- Wireshark
- Python
- Git/GitHub
- Zeek
- Suricata
- Security Onion

> Tools are added to the project as they are actually deployed and tested.

## Project Goals

- Build an isolated cybersecurity lab network
- Configure and administer a Linux server
- Practice Linux security and system hardening
- Collect and analyze security logs
- Deploy a SIEM
- Create security detections
- Investigate simulated security events
- Practice incident response
- Learn network security monitoring
- Document troubleshooting and lessons learned

## Project Phases

### Phase 1 — Network Infrastructure

- [x] Configure GL-SFT1200 as dedicated lab router
- [x] Create separate private lab network
- [x] Configure secure wireless access
- [ ] Verify network segmentation
- [ ] Document firewall configuration
- [ ] Create network architecture diagram

### Phase 2 — Raspberry Pi Linux Server

- [x] Install Ubuntu Server
- [x] Connect server to lab wireless network
- [ ] Configure hostname
- [ ] Configure SSH
- [ ] Create/verify administrative account
- [ ] Apply system updates
- [ ] Harden SSH
- [ ] Configure system logging

### Phase 3 — SIEM / Centralized Logging

- [ ] Deploy Splunk
- [ ] Configure log collection
- [ ] Forward Raspberry Pi logs
- [ ] Build searches
- [ ] Create dashboards
- [ ] Create alerts

### Phase 4 — Detection Engineering

Planned detections include:

- Failed SSH authentication
- Repeated authentication attempts
- Successful login after repeated failures
- Suspicious process activity
- Unusual network connections
- Other Linux security events

### Phase 5 — Incident Investigation

Each investigation will document:

1. Alert/event
2. Initial triage
3. Relevant logs
4. Indicators and evidence
5. Timeline
6. Analysis
7. Findings
8. Recommended remediation

## Example Investigation Workflow

```text
Security Event
      │
      ▼
Log Collection
      │
      ▼
SIEM Detection
      │
      ▼
Alert
      │
      ▼
SOC Triage
      │
      ▼
Investigation
      │
      ▼
Findings
      │
      ▼
Remediation
```

## Network Security Approach

The lab is designed as a separate network behind the existing home gateway.

```text
Home Network
     │
     │
     ▼
Lab Router
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

- Configuration problems
- Troubleshooting steps
- Networking concepts learned
- Security decisions
- Detection tuning
- Incident investigation findings

## Skills Demonstrated

- Network configuration
- Network segmentation
- Linux administration
- SSH administration
- System hardening
- Log analysis
- SIEM
- Detection engineering
- Network security monitoring
- Incident response
- Technical documentation
- Git/GitHub

## Project Status

**Current focus:** Building the lab network and Raspberry Pi Linux server.

Future updates will document the deployment, configuration, detections, investigations, and lessons learned as the lab develops.
README.md
Displaying README.md.
