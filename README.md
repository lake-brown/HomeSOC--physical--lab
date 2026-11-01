# 🛡️ HomeSOC-Lab

**Status:** In Progress
**Project Type:** Cybersecurity Homelab / Security Operations Lab
**Focus Areas:** Networking | Linux Administration | Active Directory | SIEM | Security Monitoring | Detection Engineering | Incident Response

---

## 📌 Overview

HomeSOC-Lab is a hands-on cybersecurity homelab designed to develop practical skills in network infrastructure, system administration, identity and access management, security monitoring, and security operations.

The environment combines physical networking equipment, Linux systems, and an isolated virtual Windows infrastructure to simulate components of a small enterprise network.

The goal is to build, configure, secure, monitor, and document an environment where I can practice deploying systems, managing identities, collecting security telemetry, investigating events, and developing security monitoring capabilities.

This project is being developed incrementally, with each component documented as it is configured, tested, and validated.

### Primary Objectives

- Build and maintain an isolated cybersecurity lab.
- Design and implement secure network segmentation.
- Configure firewall, NAT, DHCP, and wireless networking.
- Deploy and administer Linux infrastructure.
- Practice Linux system hardening and secure remote administration.
- Build and administer a Windows Server and Active Directory environment.
- Manage users, groups, Organizational Units, and Group Policy.
- Automate administrative tasks using PowerShell.
- Establish centralized logging and security monitoring.
- Collect and analyze endpoint and network telemetry.
- Develop security detections and investigation workflows.
- Practice incident response and security validation.
- Maintain professional technical documentation.

---

## 🏗️ Lab Architecture

#### Physical Infrastructure

The physical lab consists of a dedicated lab router, Raspberry Pi Ubuntu Server, Lenovo Ubuntu workstation, and HP Pavilion laptop hosting the virtual Windows environment.

```
                         Internet
                            |
                     Home Gateway
                            |
                     Dedicated Lab Router
                       Firewall / NAT
                            |
                       Private Lab LAN
                            |
              +-------------+-------------+
              |             |             |
           Lenovo       Raspberry Pi   HP Pavilion
           Ubuntu       Ubuntu Server    Laptop
           Desktop          |               |
              |             |           VMware
          Security       Monitored       Workstation
          Workstation     Endpoint           |
              |                          Virtual Lab
          Splunk /                          |
          Wireshark                 +--------+--------+
                                    |                 |
                               Windows Server   Windows Client
                                  Domain             VM
                                Controller
                                    |
                             Active Directory
                                    |
                              Users / Groups
                                    |
                              Organizational
                                    Units
                                    |
                              Group Policy
                                    |
                            PowerShell Automation
```

Network Isolation

The physical lab operates behind a dedicated lab router, creating a separate network from the normal home network.

The Windows virtual environment operates on a dedicated VMware virtual network and is initially isolated from the physical lab network.

The separation is intended to:

- Reduce unnecessary exposure of lab systems.
- Prevent unintended DHCP interactions between environments.
- Keep Windows testing isolated from the physical infrastructure.
- Allow controlled testing of network and security configurations.
- Support future integration with centralized logging and monitoring.

Any future connectivity between the physical and virtual environments will be deliberately configured, tested, and documented.

---

### 💻 Hardware

| Device                    | Role                                                 |
| ------------------------- | ---------------------------------------------------- |
| Dedicated Lab RouterLab   | firewall, NAT gateway, DHCP, and wireless networking |
| Raspberry Pi 3A+          | Ubuntu Server and monitored endpoint                 |
| Lenovo IdeaPad            | Ubuntu security workstation                          |
| HP Pavilion Gaming Laptop | VMware Workstation Pro host                          |
| Home Gateway              | Upstream Internet connection and home network        |

---

### 🧰 Technology Stack

The following technologies are part of the lab environment or planned implementation.

Network Infrastructure

- Dedicated lab router
- Firewall
- NAT
- DHCP
- Wireless networking
- Network segmentation
- SSH
- TCP/IP
  Operating Systems
- Ubuntu Server
- Ubuntu Desktop
- Windows Server
- Windows Client
  Identity and Access Management
- Active Directory Domain Services (AD DS)
- DNS
- Organizational Units (OUs)
- User and security group management
- Group Policy
- PowerShell administration
- Automated user provisioning
- Windows security event auditing
  Security Monitoring
- Splunk
- Wazuh
- Suricata
- Zeek
- Wireshark
- Security Onion
  Development and Documentation
- Python
- Bash
- PowerShell
- Git
- GitHub
- Markdown

## Deployment policy: Tools and technologies are only considered deployed or demonstrated after they have been configured, tested, and documented. Planned technologies are not represented as completed implementations.

### 🎯 Project Goals

[x] Build an isolated physical cybersecurity lab.
[x] Configure dedicated lab networking infrastructure.
[x] Establish a private lab LAN.
[x] Configure firewall, NAT, and DHCP.
[x] Implement and test network segmentation.
[x] Deploy Ubuntu Server on Raspberry Pi.
[x] Build an isolated Windows virtual environment.
[x] Configure Windows Server and Active Directory.
[x] Create test users, groups, and OUs.
[x] Configure and test Group Policy.
[x] Develop PowerShell user provisioning scripts.
[ ] Complete Linux server hardening.
[ ] Establish centralized logging.
[ ] Deploy endpoint monitoring.
[ ] Deploy network security monitoring.
[ ] Integrate security telemetry into a SIEM.
[ ] Develop security detections and dashboards.
[ ] Validate security controls.
[ ] Complete final documentation and assessment.

---

### 📋 Project Roadmap

Phase 1 — Network Infrastructure

Status: Completed

Focus: Build and secure the isolated physical lab network.
[x] Configure dedicated lab router.
[x] Establish private lab LAN.
[x] Configure lab wireless network.
[x] Review wireless security.
[x] Configure and review firewall rules.
[x] Verify NAT configuration.
[x] Verify DHCP configuration.
[x] Create router configuration backup.
[x] Test network segmentation.
[x] Document network architecture.

Phase 1 Deliverables

- Physical network architecture.
- Dedicated lab router configuration.
- Private lab network.
- Firewall and NAT configuration.
- DHCP configuration.
- Network segmentation validation.
- Router configuration backup.

---

Phase 2 — Linux Infrastructure and Hardening

Status: In Progress

Focus: Deploy, administer, and secure the Raspberry Pi Ubuntu Server.

Installation and Configuration
[x] Install Ubuntu Server.
[x] Connect Raspberry Pi to lab network.
[ ] Complete hostname configuration.
[ ] Document network configuration.
[ ] Verify administrative access.
[ ] Create and verify administrative accounts.
[ ] Verify administrative group membership.
System Administration
[ ] Apply and document system updates.
[ ] Configure file and directory permissions.
[ ] Review users and groups.
[ ] Review system services.
[ ] Review listening services and ports.
[ ] Configure system logging.
SSH and Remote Administration
[ ] Verify SSH configuration.
[ ] Test secure remote access.
[ ] Review SSH authentication settings.
[ ] Harden SSH configuration.
[ ] Validate remote administrative access.
Host Security
[ ] Configure UFW host firewall.
[ ] Review allowed network connections.
[ ] Apply Linux security hardening.
[ ] Validate file permissions.
[ ] Document system security baseline.

Phase 2 Deliverables

- Ubuntu Server installation documentation.
- Linux administration documentation.
- SSH configuration and hardening documentation.
- User and group configuration.
- Firewall configuration.
- System service review.
- Linux security baseline.

---

Phase 3 — Windows Server and Active Directory

Status: Completed

Focus: Build an isolated virtual Windows environment and practice identity and access management.

Virtual Infrastructure
[x] Create dedicated VMware virtual network.
[x] Install Windows Server.
[x] Configure isolated Windows environment.
[x] Configure test domain.
[x] Configure DNS for the test domain.
Active Directory
[x] Install Active Directory Domain Services.
[x] Create organizational unit structure.
[x] Create test users.
[x] Create security groups.
[x] Configure user and group management.
[x] Configure Group Policy.
[x] Test Group Policy behavior.
PowerShell Automation
[x] Create PowerShell provisioning scripts.
[x] Prepare sample CSV user data.
[x] Import test users from CSV.
[x] Automate user account creation.
[x] Validate created accounts.
Windows Client Integration
[x] Configure Windows client VM.
[x] Join client to test domain.
[x] Test domain user logons.
[x] Test group-based access.
[x] Review Windows security events.
Documentation
[x] Document Windows Server installation.
[x] Document Active Directory configuration.
[x] Document DNS configuration.
[x] Document OU and group structure.
[x] Document PowerShell scripts.
[x] Document testing and troubleshooting.

Phase 3 Deliverables

- Windows Server installation.
- Active Directory domain.
- DNS configuration.
- Organizational Unit structure.
- Test users and security groups.
- Group Policy configuration.
- PowerShell automation.
- Windows client domain integration.
- Security event review.

## Detailed Windows documentation is maintained separately in the windows-server-ad/ directory.

Phase 4 — Security Monitoring Infrastructure

Status: Planned

Focus: Establish endpoint and network security monitoring.

Telemetry Planning
[ ] Define security telemetry requirements.
[ ] Identify monitored endpoints.
[ ] Identify relevant network traffic.
[ ] Document logging architecture.
[ ] Define monitoring objectives.
Endpoint Monitoring
[ ] Deploy Wazuh.
[ ] Configure endpoint monitoring.
[ ] Connect monitored Linux endpoint.
[ ] Evaluate Windows endpoint monitoring.
[ ] Verify security event collection.
[ ] Review endpoint alerts.
Network Monitoring
[ ] Deploy Suricata.
[ ] Configure network monitoring.
[ ] Evaluate Zeek deployment.
[ ] Review network security events.
[ ] Validate network telemetry visibility.
Documentation
[ ] Document monitoring architecture.
[ ] Document endpoint configuration.
[ ] Document network monitoring configuration.
[ ] Document collected security events.
[ ] Validate telemetry visibility.
Phase 4 Deliverables

- Endpoint monitoring infrastructure.
- Network monitoring infrastructure.
- Security telemetry collection.
- Initial security alerts.
- Monitoring architecture documentation.

---

Phase 5 — SIEM and SOC Integration

Status: Planned

Focus: Centralize security telemetry and establish the SOC monitoring layer.

Splunk Deployment
[ ] Deploy and configure Splunk.
[ ] Configure data inputs.
[ ] Establish log collection.
[ ] Verify log ingestion.
[ ] Configure relevant data sources.
Log Forwarding
[ ] Forward Raspberry Pi system logs.
[ ] Integrate relevant Linux security events.
[ ] Evaluate Windows event forwarding.
[ ] Integrate relevant Windows security events.
[ ] Integrate Wazuh telemetry.
[ ] Integrate Suricata telemetry.
SIEM Development
[ ] Create security searches.
[ ] Create monitoring dashboards.
[ ] Configure initial alerts.
[ ] Review security events.
[ ] Develop detection use cases.
[ ] Tune detections and reduce false positives.
Integration Validation
[ ] Validate Wazuh and Splunk integration.
[ ] Validate Suricata and Splunk integration.
[ ] Verify event timestamps and fields.
[ ] Verify log ingestion.
[ ] Document end-to-end data flow.

Phase 5 Deliverables

- Centralized logging infrastructure.
- Splunk deployment.
- Integrated security telemetry.
- SIEM searches and dashboards.
- Initial security alerts.
- Detection use cases.
- Data flow documentation.

---

Phase 6 — Validation, Documentation and Assessment

Status: Planned

Focus: Validate security controls and document the completed lab.

Network Validation
[ ] Perform network security validation.
[ ] Verify firewall behavior.
[ ] Validate network segmentation.
[ ] Review exposed services.
[ ] Document network security findings.
Linux Validation
[ ] Validate Linux hardening.
[ ] Validate SSH security.
[ ] Review user permissions.
[ ] Verify firewall configuration.
[ ] Review system logging.
Windows Validation
[ ] Validate Active Directory users.
[ ] Validate security groups.
[ ] Validate Group Policy.
[ ] Review Windows security auditing.
[ ] Verify domain client functionality.
Monitoring Validation
[ ] Verify endpoint telemetry.
[ ] Verify network telemetry.
[ ] Verify SIEM ingestion.
[ ] Test security event visibility.
[ ] Validate alert generation.
[ ] Document detection results.
Final Documentation
[ ] Finalize architecture diagrams.
[ ] Review and redact screenshots.
[ ] Document troubleshooting.
[ ] Document lessons learned.
[ ] Complete final lab assessment.
[ ] Review and organize GitHub repository.

Phase 6 Deliverables

- Security validation documentation.
- Network testing results.
- Linux hardening assessment.
- Active Directory validation.
- SIEM integration testing.
- Security monitoring assessment.
- Final project documentation.

---

### 📂 Repository Structure

The repository is organized to separate the main lab architecture from individual infrastructure projects.

```
HomeSOC-Lab/
│
├── README.md
│
├── documentation/
│   ├── network-architecture/
│   ├── network-security/
│   ├── linux-administration/
│   ├── linux-hardening/
│   ├── security-monitoring/
│   ├── siem/
│   └── incident-response/
│
├── linux-server/
│   ├── README.md
│   ├── documentation/
│   ├── configuration/
│   └── screenshots/
│
├── windows-server-ad/
│   ├── README.md
│   ├── documentation/
│   ├── powershell/
│   ├── sample-data/
│   └── screenshots/
│
├── security-monitoring/
│   ├── wazuh/
│   ├── suricata/
│   ├── zeek/
│   └── documentation/
│
├── splunk/
│   ├── configuration/
│   ├── searches/
│   ├── dashboards/
│   ├── alerts/
│   └── documentation/
│
├── scripts/
│   ├── bash/
│   ├── python/
│   └── powershell/
│
└── screenshots/
    ├── network/
    ├── linux/
    ├── windows/
    └── monitoring/
```

Directories will be populated as the corresponding components are implemented.

### 🪟 Windows Virtual Lab Structure

The Windows Server and Active Directory environment is maintained separately to keep its configuration, scripts, and documentation organized.

```
windows-server-ad/
├── README.md
├── documentation/
│   ├── installation.md
│   ├── active-directory.md
│   ├── dns-configuration.md
│   ├── organizational-units.md
│   ├── group-policy.md
│   └── testing.md
│
├── powershell/
│   ├── create-users.ps1
│   ├── create-groups.ps1
│   └── user-provisioning.ps1
│
├── sample-data/
│   └── sample-users.csv
│
└── screenshots/
    ├── server-installation/
    ├── active-directory/
    ├── group-policy/
    └── client-domain-join/
```

The Windows Server README contains the detailed build guide, configuration steps, PowerShell scripts, testing results, and screenshots.

The main README provides the overall project architecture and roadmap.

### 🔐 Network Security Approach

The physical lab is designed as a separate network behind the home gateway.

A dedicated lab router provides the lab network with firewall, NAT, DHCP, and wireless networking capabilities.

The Windows virtual environment initially operates on its own dedicated VMware virtual network.

Security Design Principles
Separate lab infrastructure from the normal home network.
Minimize unnecessary network exposure.
Use firewall rules to control network communication.
Keep the Windows virtual environment isolated initially.
Avoid unintended DHCP interactions.
Use secure remote administration.
Validate network segmentation through controlled testing.
Document changes to network architecture.
Introduce connectivity between environments only when required.

Firewall behavior and network segmentation will be tested and documented rather than assumed.

### 🛡️ Security and Privacy

This repository intentionally excludes sensitive information.

The following information will not be published:

Real public IP addresses.
Real home-network IP addresses.
Wi-Fi passwords.
SSH passwords.
Administrator passwords.
API keys.
Private keys.
MAC addresses.
Authentication tokens.
Personal network identifiers.

Screenshots will be reviewed and redacted before publication.

All sample data will use fictional identities and documentation-only values.

Example Configuration Placeholders
text
LAB_ROUTER_IP=<LAB_ROUTER_IP>
SERVER_IP=<SERVER_IP>
WORKSTATION_IP=<WORKSTATION_IP>
HOME_GATEWAY_IP=<HOME_GATEWAY_IP>

No real credentials or sensitive network information should be committed to the repository.

📚 Lessons Learned

This section will document technical challenges, troubleshooting procedures, and improvements discovered throughout the project.

Topics include:

Networking
Router configuration challenges.
Firewall behavior.
NAT and DHCP troubleshooting.
Network segmentation.
Wireless security.
Network connectivity issues.
Linux Administration
Ubuntu Server configuration.
SSH troubleshooting.
User and group management.
File permissions.
Firewall configuration.
System service management.
System logging.
Windows Administration
Windows Server installation.
Active Directory configuration.
DNS troubleshooting.
User and group management.
Group Policy troubleshooting.
PowerShell automation.
Windows security event auditing.
Security Monitoring
Log collection challenges.
Telemetry visibility.
SIEM integration.
Detection tuning.
False positives.
Alert investigation.
Monitoring improvements.

Lessons learned will be added as each component is deployed and tested.

🧠 Skills Developed and Demonstrated

The following skills are associated with the project. Their status reflects the actual implementation and validation of each component.

Networking

Demonstrated:

Network segmentation.
TCP/IP fundamentals.
DHCP.
NAT.
Firewall configuration.
Wireless security.
Network troubleshooting.

Further development:

Network reconnaissance.
Network traffic analysis.
Intrusion detection.
Network security monitoring.
Linux Administration

Demonstrated:

Ubuntu Server installation.
Ubuntu Desktop administration.
Linux infrastructure deployment.

In Progress:

SSH administration.
User and group management.
File permissions and ACLs.
UFW.
System services.
System logging.
Linux system hardening.
Identity and Access Management

Demonstrated:

Active Directory Domain Services.
User and group administration.
Organizational Units.
Group Policy.
PowerShell user provisioning.
Windows domain integration.
Windows security event review.
Security Operations

Planned:

SIEM administration.
Log analysis.
Alert triage.
Endpoint monitoring.
Network security monitoring.
Intrusion detection.
Detection engineering.
Threat investigation.
Incident response.
Security Tools
Splunk.
Wazuh.
Suricata.
Wireshark.
Nmap.
Active Directory administration tools.
PowerShell.

Individual tool proficiency will be documented as technologies are configured and tested.

Development and Documentation
Bash.
Python.
PowerShell.
Git.
GitHub.
Markdown.
Technical documentation.
Security reports.
Investigation reports.

### 📊 Project Status

Overall Status: In Progress

Project Phase Status
Phase 1 — Network Infrastructure Completed
Phase 2 — Linux Infrastructure and Hardening In Progress
Phase 3 — Windows Server and Active Directory Completed
Phase 4 — Security Monitoring Infrastructure Planned
Phase 5 — SIEM and SOC Integration Planned
Phase 6 — Validation and Assessment Planned
Current Focus

The immediate priority is completing the Raspberry Pi Ubuntu Server configuration and hardening process.

Upcoming tasks include:

Complete hostname and administrative configuration.
Verify and secure SSH access.
Apply system updates.
Configure administrative accounts and permissions.
Configure UFW.
Review listening services and system logging.
Document the Linux security baseline.

After Linux hardening is completed, the next major objective is establishing endpoint and network security monitoring.

The Windows Server and Active Directory environment has been built and documented separately.

Future updates will document verified deployments, configurations, security detections, investigations, and lessons learned.

🚀 Project Philosophy

HomeSOC-Lab is designed around practical implementation rather than simply installing tools or following tutorials.

Each component should have:

A documented purpose.
A clear configuration process.
A security justification.
A validation procedure.
Documented test results.
Troubleshooting notes.
Supporting screenshots where appropriate.

The goal is to develop practical cybersecurity knowledge through building, securing, monitoring, testing, and documenting a functioning lab environment.

Build it. Secure it. Monitor it. Investigate it. Document it.

HomeSOC-Lab — An ongoing hands-on cybersecurity project focused on developing practical infrastructure, Linux administration, identity and access management, security monitoring, and SOC analyst skills.
