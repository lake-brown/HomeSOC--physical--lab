# IAM Lifecycle & RBAC Lab

## Overview

This project is a hands-on Identity and Access Management (IAM) lab built within my HomeSOC environment.

The lab demonstrates core IAM processes including:

- Identity and account management
- Authentication and authorization
- Role-Based Access Control (RBAC)
- Least privilege
- User lifecycle management
- Access requests and approvals
- Access reviews
- Privileged access management concepts
- IAM auditing and documentation

The goal is to simulate common IAM Analyst responsibilities in a controlled environment.

---

## Lab Environment

The IAM lab uses the existing HomeSOC network architecture.

```text
Internet
   │
Home Router
   │
Dedicated Lab Router
Private Lab LAN
   │
   ├── Lenovo Ubuntu Desktop
   │      └── IAM Administration / Testing
   │
   └── Ubuntuserver
          └── Raspberry Pi 3A+
              Ubuntu Server
              IAM Server
```

### Systems

| System                | Role                                       |
| --------------------- | ------------------------------------------ |
| Lenovo Ubuntu Desktop | IAM administration and testing workstation |
| `Ubuntuserver`        | IAM server                                 |
| `admin`               | Dedicated administrative account           |
| Dedicated Lab Router  | Network security boundary                  |
| UFW                   | Host-based firewall                        |

---

## IAM Security Objectives

The lab is designed around the following principles:

### Authentication

Verify the identity of users attempting to access systems and resources.

### Authorization

Determine what an authenticated user is permitted to access.

### RBAC

Assign permissions according to job responsibilities rather than individually assigning every permission.

### Least Privilege

Users should receive only the access required to perform their responsibilities.

### Lifecycle Management

Manage identities throughout the user lifecycle:

```text
Joiner → Mover → Leaver
```

### Access Governance

Document and review access requests, approvals, role changes, and privileged access.

### Auditability

Maintain evidence of identity and access decisions so activity can be reviewed.

---

## Project Phases

### Phase 1 — IAM Foundation

- Linux server configuration
- Dedicated administrative account
- SSH administration
- Host firewall
- Network verification
- IAM architecture
- Security documentation

**Status: Complete**

### Phase 2 — Identity Directory

- Users
- Groups
- Departments
- Administrative groups
- Service accounts
- Identity naming standards

**Status: Planned**

### Phase 3 — RBAC

- Employee role
- Manager role
- IT Support role
- IAM Analyst role
- IAM Administrator role
- Application Administrator role
- Role-to-group mapping
- Permission assignments

**Status: Planned**

### Phase 4 — User Lifecycle

- Joiner process
- Mover process
- Leaver process
- Access provisioning
- Access modification
- Access revocation

**Status: Planned**

### Phase 5 — Access Governance

- Access requests
- Approvals
- Access reviews
- Privileged access reviews
- Least-privilege validation
- Group membership reviews

**Status: Planned**

### Phase 6 — Documentation & Portfolio

- IAM procedures
- Access review reports
- Lifecycle documentation
- Architecture documentation
- Audit evidence
- Troubleshooting procedures

**Status: Planned**

---

## Phase 1 Security Controls

The server foundation includes:

- Dedicated administrative account
- Sudo-based privilege elevation
- SSH remote administration
- UFW host firewall
- Default inbound traffic denied
- Explicit SSH access
- System updates and upgrades
- Verified network configuration

SSH access is currently permitted through TCP port 22 for administrative access.

The HomeSOC dedicated router provides an additional network security boundary around the lab environment.

---

## IAM Design Principles

The project follows these core IAM principles:

1. **Least privilege**
2. **Role-based access**
3. **Separation of duties**
4. **Controlled administrative access**
5. **Lifecycle-based identity management**
6. **Access review**
7. **Auditability**
8. **Documented procedures**

---

## Future Enhancements

Future phases will introduce a dedicated identity directory and additional IAM capabilities while keeping the implementation appropriate for the available lab hardware.

The project will document the actual technologies and controls implemented rather than claiming experience with enterprise IAM platforms that are not deployed in this lab.
