# Active Directory & PowerShell Automation Lab

**Status:** In Progress  
**Focus:** Identity and Access Management (IAM) | Active Directory | Windows Server | PowerShell Automation | Security Monitoring

## 1. Overview

This project expands my physical HomeSOC lab by introducing a Windows Server environment focused on Active Directory administration, Identity and Access Management (IAM), and PowerShell automation.

The objective is to build a virtualized Windows domain environment that simulates common enterprise identity management and Windows administration operations.

Using Windows Server and VMware Workstation Pro, I will configure Active Directory Domain Services (AD DS), manage domain users and security groups, create Organizational Units (OUs), automate user provisioning with PowerShell, and implement security policies through Group Policy.

This project complements my existing HomeSOC infrastructure, which includes an isolated lab network, an Ubuntu workstation, and a Raspberry Pi Ubuntu Server.

## 2. Lab Environment

### Host Hardware

| Component               | Specification           |
| ----------------------- | ----------------------- |
| Host Machine            | HP Pavilion             |
| Memory                  | 16 GB RAM               |
| Available Storage       | 150+ GB                 |
| Virtualization Software | VMware Workstation Pro  |
| Server Operating System | Windows Server 2022     |
| Client Operating System | Windows 10/11 (Planned) |

### Virtual Machine Specifications

| Component       | Configuration          |
| --------------- | ---------------------- |
| VM Name         | Windows-Server-AD      |
| RAM             | 4 GB                   |
| CPU             | 2 Cores                |
| Storage         | 60 GB                  |
| Firmware        | UEFI                   |
| Network Adapter | VMware Virtual Network |

_Virtual machine specifications may be adjusted based on performance and available host resources._

## 3. Network Architecture

The Windows Server environment will be integrated into my existing HomeSOC infrastructure.

### Existing Physical Infrastructure

- Home Router
- Dedicated Lab Router
- Private Lab LAN
- Lenovo Ubuntu Desktop
- Raspberry Pi Ubuntu Server

### Planned Windows Infrastructure

- Windows Server 2022 Domain Controller
- Active Directory Domain Services
- Windows domain client
- PowerShell administration environment

### Network Topology

```text
                    Home Router
                         |
                Dedicated Lab Router
                    Firewall/NAT
                         |
                    Private Lab LAN
                         |
             +-----------+-----------+
             |           |           |
           Lenovo      Raspberry    HP Pavilion
           Ubuntu      Pi Ubuntu       Host
           Desktop     Server           |
             |                       VMware
         Splunk /                  Workstation
         Wireshark                     |
                              +--------+--------+
                              |                 |
                         Windows Server    Windows Client
                         Domain Controller   (Planned)
                              |
                         Active Directory
                              |
                        Users / Groups / OUs
                              |
                        PowerShell Automation
                              |
                          Group Policy
```

_This diagram represents the planned architecture. Virtual network connectivity and integration will be validated during implementation._

## 4. Windows Server Deployment

**Objective:** Deploy Windows Server 2022 in VMware Workstation Pro and prepare it for Active Directory configuration.

### Implementation Steps

1. Download Windows Server 2022 Evaluation ISO.
2. Create a Windows Server virtual machine.
3. Allocate CPU, RAM, and storage.
4. Install Windows Server 2022.
5. Configure the Administrator account.
6. Rename the server.
7. Configure network settings.
8. Verify network connectivity.

### Screenshots

**Virtual Machine Configuration**

![VM Configuration](screenshots/vm-configuration.png)

**Windows Server Installation**

![Windows Server Installation](screenshots/windows-server-installation.png)

**Server Manager**

![Server Manager](screenshots/server-manager.png)

## 5. Active Directory Domain Services Configuration

**Objective:** Install and configure Active Directory Domain Services to establish a centralized identity management environment.

### Implementation Steps

1. Install the Active Directory Domain Services (AD DS) role.
2. Configure DNS integration.
3. Promote Windows Server to a Domain Controller.
4. Create an Active Directory domain.
5. Configure domain administrator access.
6. Verify Domain Controller functionality.
7. Test domain authentication.

### Screenshots

**AD DS Installation**

![AD DS Installation](screenshots/ad-ds-installation.png)

**Domain Controller Configuration**

![Domain Controller](screenshots/domain-controller.png)

## 6. Identity and Access Management (IAM)

**Objective:** Practice enterprise identity lifecycle management by creating and managing domain accounts, groups, and organizational structures.

### User Provisioning

- Create domain user accounts.
- Configure user attributes.
- Organize accounts into Organizational Units.
- Assign security group memberships.
- Configure account permissions.

### Organizational Units (OUs)

Organizational Units will be used to organize users and computers based on administrative or departmental requirements.

Planned examples:

- IT Department
- Human Resources
- Finance
- Security Operations
- Administration

### Group Management

- Create Active Directory security groups.
- Assign users to appropriate groups.
- Manage group memberships.
- Apply permissions based on job responsibilities.
- Practice least-privilege access.

### Identity Lifecycle Management

Practice common IAM operations:

- User provisioning
- Account modification
- Password resets
- Account disabling
- User deprovisioning
- Group membership reviews
- Access verification

### Screenshots

**Active Directory Users and Computers**

![Active Directory Users](screenshots/active-directory-users.png)

**Organizational Units**

![Organizational Units](screenshots/organizational-units.png)

**Security Groups**

![Security Groups](screenshots/security-groups.png)

## 7. PowerShell Automation

**Objective:** Automate repetitive Active Directory administration tasks using PowerShell.

### Planned Automation

| Script                            | Purpose                                 |
| --------------------------------- | --------------------------------------- |
| `create-users.ps1`                | Automate bulk user provisioning         |
| `create-organizational-units.ps1` | Create Organizational Units             |
| `create-groups.ps1`               | Create Active Directory security groups |
| `audit-users.ps1`                 | Retrieve and review user accounts       |
| `disable-users.ps1`               | Automate account disabling              |

### Automation Goals

- Reduce manual account creation.
- Standardize user provisioning.
- Automate group membership management.
- Generate user account reports.
- Improve administrative efficiency.
- Support consistent IAM procedures.

### Screenshots

**PowerShell User Provisioning**

![PowerShell Automation](screenshots/powershell-automation.png)

**Automated Active Directory Accounts**

![Automated Users](screenshots/automated-users.png)

## 8. Group Policy and Security

**Objective:** Implement security policies to control user access and strengthen domain security.

### Planned Security Configurations

- Configure password policies.
- Implement account lockout policies.
- Restrict administrative privileges.
- Apply user-specific security settings.
- Configure computer security policies.
- Implement least-privilege principles.
- Manage access through security groups.

### Group Policy Objectives

Use Group Policy Objects (GPOs) to centrally manage security settings and user configurations across domain-joined systems.

### Screenshots

**Group Policy Management**

![Group Policy](screenshots/group-policy.png)

**Security Policy Configuration**

![Security Policies](screenshots/security-policies.png)

## 9. Windows Client Integration

**Objective:** Join a Windows client to the Active Directory domain and verify centralized authentication.

### Implementation Steps

1. Deploy a Windows client virtual machine.
2. Configure network connectivity.
3. Configure DNS to use the Domain Controller.
4. Join the Windows client to the domain.
5. Authenticate using a domain user account.
6. Verify user permissions.
7. Confirm Group Policy application.
8. Troubleshoot authentication issues.

### Verification

Use Windows command-line utilities to verify domain membership and network configuration.

Examples:

- `ipconfig /all`
- `whoami`
- `gpresult /r`
- `nltest /dsgetdc:<domain>`

### Screenshots

**Joining Windows Client to Domain**

![Domain Join](screenshots/domain-join.png)

**Domain User Authentication**

![Domain Authentication](screenshots/domain-authentication.png)

## 10. Security Monitoring and Event Analysis

**Objective:** Expand the HomeSOC environment by exploring Windows authentication monitoring and security event analysis.

### Planned Activities

- Review Windows Security Event Logs.
- Investigate successful authentication events.
- Investigate failed login attempts.
- Monitor account creation and modification.
- Review account lockout events.
- Identify suspicious authentication activity.
- Explore forwarding Windows security events to Splunk.

### Windows Security Events of Interest

| Event ID | Description                             |
| -------- | --------------------------------------- |
| 4624     | Successful account logon                |
| 4625     | Failed logon attempt                    |
| 4720     | User account created                    |
| 4722     | User account enabled                    |
| 4725     | User account disabled                   |
| 4728     | Member added to a global security group |
| 4732     | Member added to a local security group  |
| 4740     | User account locked out                 |

_Event visibility depends on the applicable Windows audit policies and logging configuration._

## 11. Skills Demonstrated

| Technical Area      | Skills                                               |
| ------------------- | ---------------------------------------------------- |
| Active Directory    | Domain administration, AD DS, DNS                    |
| IAM                 | User provisioning, deprovisioning, access management |
| PowerShell          | Scripting, automation, account auditing              |
| Access Control      | RBAC, security groups, least privilege               |
| Windows Server      | Server administration and configuration              |
| Group Policy        | Centralized security policy management               |
| Networking          | DNS, IP addressing, virtual networking               |
| Security Monitoring | Windows Event Logs, authentication analysis          |
| Troubleshooting     | Domain connectivity and authentication               |

## 12. Future Enhancements

After completing the initial implementation, I plan to expand the environment with:

- Integrate Windows Security Event Logs with Splunk.
- Implement additional PowerShell IAM automation.
- Explore privileged access management (PAM).
- Configure file server permissions and auditing.
- Implement additional domain security policies.
- Explore Windows endpoint monitoring.
- Expand identity threat detection capabilities.

## 13. Project Goals

This project is designed to develop practical experience with enterprise identity infrastructure, Windows Server administration, and security operations.

By completing this lab, I aim to demonstrate the ability to:

- Administer Active Directory environments.
- Manage user identities and access permissions.
- Automate identity lifecycle operations.
- Implement centralized security policies.
- Troubleshoot Windows authentication issues.
- Analyze Windows security events.
- Understand how identity infrastructure supports enterprise cybersecurity.

---

**Project:** HomeSOC Physical Lab  
**Focus:** Active Directory | IAM | PowerShell | Windows Server | Security Operations

**Status:** In Progress
