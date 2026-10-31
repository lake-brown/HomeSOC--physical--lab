HomeSOC-Lab
Status: In Progress

A hands-on cybersecurity homelab for practicing network segmentation, Linux administration, identity and access management, centralized logging, security monitoring, detection engineering, and incident response.
Overview
HomeSOC-Lab is an isolated cybersecurity lab built with physical networking, Linux systems, and planned virtual Windows infrastructure. The goal is to create a realistic environment where I can deploy systems, manage identities, collect security telemetry, investigate events, and document the process like a SOC analyst.

The project is being built incrementally, with each component documented as it is configured and tested.
Lab Architecture
Physical Lab
Internet
|
v
+--------------------+
| Home Gateway |
| Main Network |
+---------+----------+
|
WAN
|
v
+--------------------+
| Dedicated Lab |
| Router |
| Firewall / NAT |
| DHCP / Wi-Fi |
+---------+----------+
|
Private Lab LAN
|
+----------+----------+
| |
v v
+------------------+ +--------------------+
| Raspberry Pi | | Lenovo IdeaPad |
| Ubuntu Server | | Ubuntu Desktop |
| Linux Server / | | SOC Workstation |
| Lab Endpoint | | Splunk / Wireshark |
+------------------+ +--------------------+
Planned Windows Virtual Lab
HP Pavilion Gaming Laptop
VMware Workstation Pro
|
Dedicated VMware
Virtual Network
|
+---------+----------+
| |
v v
+-------------------+ +-------------------+
| Windows Server | | Windows Client |
| Active Directory | | Domain-Joined |
| DNS / Group Policy| | Test Endpoint |
+-------------------+ +-------------------+
The Windows virtual environment will initially be kept on a dedicated VMware virtual network, separate from the physical lab network. Any later connection or log forwarding will be planned, configured, and tested deliberately.
Privacy note: Real IP addresses, Wi-Fi credentials, passwords, MAC addresses, and other sensitive network information are intentionally excluded from this repository. Examples use placeholders or documentation-only values.

Hardware
Device Role
Dedicated Lab Router Lab firewall, NAT gateway, DHCP, and wireless networking
Raspberry Pi 3A+ Ubuntu Server / monitored endpoint
Lenovo IdeaPad Ubuntu security workstation
HP Pavilion Gaming Laptop VMware Workstation Pro host for the planned Windows virtual lab
Home Gateway Upstream Internet connection and home network

Technology Stack
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
- Windows Server (planned)
- Windows client VM (planned)
  Identity & Access Management — Planned
- Active Directory Domain Services (AD DS)
- DNS for the test domain
- Organizational Units (OUs)
- User and security group management
- Group Policy
- PowerShell administration and user provisioning
- Windows security event auditing
  Security Monitoring
- Splunk
- Wazuh
- Suricata
- Zeek
- Wireshark
- Security Onion
  Development & Documentation
- Python
- Bash
- PowerShell
- Git
- GitHub
- Markdown
  Tools and skills are identified as deployed or demonstrated only after they have actually been configured, tested, and documented. Items marked planned are not yet deployed.

Project Goals

- Build an isolated physical cybersecurity lab.
- Design and document a secure network architecture.
- Configure a dedicated lab router.
- Practice firewall and NAT configuration.
- Implement network segmentation.
- Deploy and administer a Linux server.
- Practice Linux system hardening and secure remote administration.
- Build a separate virtual Windows Server and Active Directory test environment.
- Practice directory users, groups, OUs, and access control.
- Automate test-user provisioning with PowerShell and sample CSV data.
- Apply and test Group Policy settings.
- Review Windows security events and plan future SIEM integration.
- Establish centralized logging and deploy security monitoring tools.
- Collect and monitor security telemetry.
- Build a foundation for detection engineering and incident response.
- Validate security controls through controlled testing.
- Document configurations, troubleshooting, and lessons learned.
  Project Phases
  Phase 1 — Network Infrastructure
  Focus: Build and secure the isolated physical lab network.
- [x] Configure dedicated lab router
- [x] Establish private lab LAN
- [x] Configure lab wireless network
- [x] Review wireless security
- [x] Configure/review firewall rules
- [x] Verify NAT configuration
- [x] Verify DHCP configuration
- [x] Create router configuration backup
- [x] Test network segmentation
- [x] Document network architecture
      Phase 2 — Linux Infrastructure & Hardening
      Focus: Deploy and secure the Raspberry Pi Ubuntu Server.
- [x] Install Ubuntu Server
- [x] Connect Raspberry Pi to lab network
- [ ] Complete and document hostname configuration
- [ ] Verify SSH configuration and secure remote access
- [ ] Verify administrative access
- [ ] Create/verify administrative accounts and group membership
- [ ] Apply and document system updates
- [ ] Configure file and directory permissions
- [ ] Configure host firewall
- [ ] Harden SSH
- [ ] Review listening services and ports
- [ ] Configure system logging
- [ ] Document Linux security baseline
      Phase 3 — Windows Server & Active Directory Lab
      Focus: Build an isolated virtual Windows environment and practice IAM administration.
- [x] Create a dedicated VMware virtual network
- [x] Install Windows Server
- [x] Configure a test domain using Active Directory Domain Services
- [x] Configure DNS for the test domain
- [x] Create an OU structure
- [x] Create test users and security groups
- [x] Configure and test Group Policy
- [x] Create PowerShell scripts for user provisioning
- [x] Import test users from sample CSV data
- [x] Configure a Windows client VM, if host resources allow
- [x] Join the client to the test domain
- [x] Test user logons and group-based access
- [x] Review Windows security events
- [x] Document the build, tests, and troubleshooting
      Phase 4 — Security Monitoring Infrastructure
      Focus: Establish endpoint and network security monitoring.
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
      Phase 5 — SIEM & SOC Integration
      Focus: Centralize security telemetry and build the SOC monitoring layer.
- [ ] Deploy/configure Splunk
- [ ] Configure data inputs
- [ ] Forward Raspberry Pi logs
- [ ] Integrate relevant security telemetry
- [ ] Evaluate Windows event forwarding/log collection after the virtual lab is established
- [ ] Verify log ingestion
- [ ] Create security searches
- [ ] Create dashboards
- [ ] Configure initial alerts
- [ ] Validate relevant Wazuh/Splunk integration
- [ ] Validate relevant Suricata/Splunk integration
- [ ] Document end-to-end data flow
      Phase 6 — Validation, Documentation & Assessment
      Focus: Validate the lab infrastructure and document the completed work.
- [ ] Perform network security validation
- [ ] Verify firewall and segmentation behavior
- [ ] Validate Linux hardening
- [ ] Validate SSH security
- [ ] Validate Active Directory users, groups, and policies
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
      Infrastructure Progression
      Phase 1 — Network Infrastructure
      |
      v
      Phase 2 — Linux Infrastructure & Hardening
      |
      v
      Phase 3 — Windows Server & Active Directory
      |
      v
      Phase 4 — Security Monitoring Infrastructure
      |
      v
      Phase 5 — SIEM & SOC Integration
      |
      v
      Phase 6 — Validation, Documentation & Assessment
      Windows Virtual Lab Structure
      The Windows Server environment will be maintained in its own folder within this repository:
      windows-server-ad/
      ├── README.md
      ├── documentation/
      ├── powershell/
      ├── sample-data/
      └── screenshots/
      The folder's README will contain the detailed Windows Server build guide, configuration steps, PowerShell scripts, test results, and screenshots. The main README provides the overall project architecture and roadmap.
      Network Security Approach
      The physical lab is designed as a separate network behind the home gateway. Its purpose is to reduce unnecessary direct exposure of lab systems to the normal home network while allowing the lab to access the Internet when required.

The Windows virtual lab will initially remain on a dedicated VMware virtual network. It will not share DHCP services with the physical lab or home network. Any future connectivity between the virtual and physical environments will be introduced only when required and documented.

Firewall behavior and segmentation will be tested and documented rather than assumed.
Security & Privacy
This repository intentionally does not contain:

- Real public IP addresses
- Real home-network IP addresses
- Wi-Fi passwords
- SSH or administrator passwords
- API keys
- Private keys
- MAC addresses
- Authentication tokens
- Personal network identifiers
  When screenshots are added, sensitive information will be redacted before publication. Sample data will use fictional users and documentation-only values.

Example placeholders:
LAB_ROUTER_IP=<LAB_ROUTER_IP>
SERVER_IP=<SERVER_IP>
WORKSTATION_IP=<WORKSTATION_IP>
HOME_GATEWAY_IP=<HOME_GATEWAY_IP>
Lessons Learned
This section will document:

- Network configuration problems
- Linux and Windows configuration problems
- Troubleshooting steps
- Firewall behavior
- Identity and access control decisions
- Monitoring challenges
- Detection tuning
- False positives
- Investigation findings
- Security improvements
  Skills Demonstrated
  Networking
- Network segmentation
- TCP/IP
- DHCP
- NAT
- Firewall configuration
- Wireless security
- Network troubleshooting
- Network reconnaissance
  Linux Administration
- Ubuntu Server administration
- SSH
- Users and groups
- File permissions and ACLs
- UFW
- System services
- System logging
- Linux hardening
  Identity & Access Management
- Active Directory Domain Services (planned)
- User and group administration (planned)
- Organizational Units (planned)
- Group Policy (planned)
- PowerShell automation (planned)
- Windows security auditing (planned)
  Security Operations
- SIEM
- Log analysis
- Alert triage
- Endpoint monitoring
- Network security monitoring
- IDS
- Detection engineering
- Threat investigation
- Incident response
  Security Tools
- Splunk
- Wazuh
- Suricata
- Wireshark
- Nmap
- Active Directory and PowerShell tools (planned)
  Documentation
- Technical documentation
- Security reports
- Investigation reports
- Git
- GitHub
- Markdown
  Project Status
  Current focus: Continue Linux server hardening and prepare the isolated Windows Server / Active Directory virtual lab.

The Windows Server environment and its IAM exercises are planned additions. They will be marked complete only after they have been configured, tested, and documented.

Future updates will document verified deployments, configurations, detections, investigations, and lessons learned as the lab develops.
