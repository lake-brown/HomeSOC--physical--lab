# HomeSOC: Active Directory & PowerShell Automation Lab

**Status:** In Progress  
**Focus:** Active Directory, Identity and Access Management (IAM), PowerShell Automation, and Windows Server Administration.

## Overview

This project expands my physical HomeSOC lab by introducing a Windows Server environment for practicing Active Directory administration, identity lifecycle management, and PowerShell automation.

Using Windows Server and VMware Workstation Pro, I will build a domain-based environment to practice managing user accounts, security groups, Organizational Units (OUs), access permissions, and Group Policy.

The project emphasizes practical IAM operations commonly performed in enterprise IT and security environments.

## Lab Environment

| Component         | Configuration           |
| ----------------- | ----------------------- |
| Host Machine      | HP Pavilion             |
| RAM               | 16 GB                   |
| Virtualization    | VMware Workstation Pro  |
| Available Storage | 150+ GB                 |
| Server OS         | Windows Server 2022     |
| Client OS         | Windows 10/11 (planned) |
| Environment       | Virtualized HomeSOC Lab |

## Project Objectives

- Deploy Windows Server in VMware.
- Install Active Directory Domain Services (AD DS).
- Configure a Domain Controller.
- Create and manage domain users.
- Organize users with Organizational Units.
- Create security groups and manage permissions.
- Automate user provisioning using PowerShell.
- Implement role-based access control (RBAC).
- Configure Group Policy Objects (GPOs).
- Practice account auditing and deprovisioning.
- Join a Windows client to the domain.
- Investigate Windows authentication events.

## Network Architecture

The Windows Server environment will complement my existing HomeSOC infrastructure.

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
          |                         |
      Splunk /                  VMware Workstation
      Wireshark                      |
                              +------+------+
                              |             |
                         Windows Server  Windows Client
                         Domain Controller  (Planned)
                              |
                         Active Directory
                              |
                       Users / Groups / OUs
                              |
                       PowerShell Automation
                              |
                         Group Policies
```

_Virtual network connectivity and integration will be validated during implementation._

## Implementation Roadmap

### Phase 1: Windows Server Deployment

- Create Windows Server virtual machine.
- Install Windows Server 2022.
- Configure hostname and networking.
- Verify network connectivity.

### Phase 2: Active Directory Configuration

- Install AD DS.
- Promote server to Domain Controller.
- Configure Active Directory domain.
- Configure and verify DNS.
- Test domain administration.

### Phase 3: Identity and Access Management

- Create Organizational Units.
- Provision domain user accounts.
- Create security groups.
- Configure group memberships.
- Apply least-privilege principles.
- Practice account disabling and deprovisioning.

### Phase 4: PowerShell Automation

- Automate bulk user provisioning.
- Automate OU creation.
- Automate security group management.
- Generate user account reports.
- Audit Active Directory accounts.

### Phase 5: Group Policy and Security

- Configure Group Policy Objects.
- Implement password policies.
- Configure account lockout policies.
- Restrict administrative privileges.
- Apply user and computer security settings.

### Phase 6: Domain Client Integration

- Deploy Windows client virtual machine.
- Configure DNS.
- Join client to Active Directory domain.
- Authenticate using domain accounts.
- Verify permissions and Group Policy application.

### Phase 7: Security Monitoring

- Review Windows Security Event Logs.
- Investigate successful and failed logins.
- Monitor account creation and modification.
- Explore forwarding Windows security events to Splunk.

## Skills Demonstrated

- Active Directory administration
- Identity lifecycle management
- User provisioning and deprovisioning
- Group and permission management
- Role-Based Access Control (RBAC)
- PowerShell automation
- Group Policy administration
- Windows Server administration
- Authentication troubleshooting
- Security event monitoring

## Repository Structure

| Directory        | Purpose                                           |
| ---------------- | ------------------------------------------------- |
| `documentation/` | Technical documentation and implementation guides |
| `powershell/`    | Active Directory automation scripts               |
| `sample-data/`   | Sample CSV files and test account data            |
| `screenshots/`   | Visual evidence of completed lab activities       |

## Future Enhancements

- Integrate Windows security events with Splunk.
- Explore privileged access management.
- Implement additional IAM automation.
- Configure file server permissions.
- Expand identity monitoring and auditing.

## Project Goals

Build practical experience with enterprise identity infrastructure, Windows administration, and security operations while expanding my existing HomeSOC physical lab.

**Project:** HomeSOC Physical Lab  
**Focus:** Active Directory | IAM | PowerShell | Windows Server | Security Operations
