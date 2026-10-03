# IAM Architecture

## Purpose

This document defines the architecture for the IAM Lifecycle and RBAC Lab.

The architecture uses the existing HomeSOC environment to provide a controlled network for identity and access management testing.

---

## Network Architecture

```text
                    Internet
                       │
                       ▼
                 Home Router
                       │
                       ▼
              Dedicated Lab Router
                Private Lab LAN
                       │
              ┌────────┴────────┐
              │                 │
              ▼                 ▼
       Lenovo Ubuntu     Raspberry Pi 3A+
       IAM Workstation     Ubuntu Server
              │                 |
              │                 │
              └────── SSH ──────┘
```

---

## System Roles

### Lenovo Ubuntu Desktop

The Lenovo Ubuntu system functions as the IAM administration and testing workstation.

Primary responsibilities:

- Administrative access
- SSH client
- Identity testing
- Access validation
- Documentation
- Future IAM testing

### `Ubuntuserver`

`Ubuntuserver` is the Raspberry Pi Ubuntu Server used as the server-side component of the IAM lab.

Primary responsibilities:

- Identity management services
- User and group management
- RBAC implementation
- Access-control testing
- IAM logging and auditing
- Lifecycle testing

### `admin`

`admin` is the dedicated administrative account used to perform authorized administrative tasks.

The account uses sudo for controlled privilege elevation rather than routinely operating as root.

### Dedicated Lab Router

The router provides network segmentation for the HomeSOC lab.

It separates the lab environment from the primary home network and provides the network boundary for the lab systems.

### UFW

UFW provides host-based firewall enforcement on `Ubuntuserver`.

Current baseline:

- Default incoming traffic: Denied
- Default outgoing traffic: Allowed
- SSH/TCP 22: Allowed
- Firewall logging: Low

---

## IAM Security Model

The project follows this general authorization model:

```text
User
  │
  ▼
Identity
  │
  ▼
Group / Role
  │
  ▼
Permission
  │
  ▼
Resource
```

The objective is to avoid assigning unnecessary permissions directly to individual users.

Instead, access will be associated with defined roles and groups.

---

## Identity Lifecycle

The architecture supports three primary identity lifecycle events:

```text
        ┌─────────┐
        │ JOINER  │
        └────┬────┘
             │
             ▼
        ┌─────────┐
        │ ACTIVE  │
        └────┬────┘
             │
             ▼
        ┌─────────┐
        │ MOVER   │
        └────┬────┘
             │
             ▼
        ┌─────────┐
        │ ACTIVE  │
        └────┬────┘
             │
             ▼
        ┌─────────┐
        │ LEAVER  │
        └─────────┘
```

Each lifecycle event will have documented access-management procedures.

---

## Authorization Principles

### Least Privilege

Users receive only the permissions required for their assigned responsibilities.

### Role-Based Access Control

Permissions will be grouped according to defined organizational roles.

### Separation of Duties

Administrative responsibilities will be separated where appropriate to reduce unnecessary concentration of privileges.

### Privileged Access

Administrative privileges will be explicitly assigned and reviewed.

### Access Reviews

Group membership and privileged access will be periodically reviewed to identify inappropriate or unnecessary access.

---

## Phase 1 Implementation Status

| Control                 | Status   |
| ----------------------- | -------- |
| Server hostname         | Complete |
| Dedicated administrator | Complete |
| Sudo authorization      | Complete |
| SSH administration      | Complete |
| Host firewall           | Complete |
| Network verification    | Complete |
| IAM architecture        | Complete |
| IAM documentation       | Complete |

---

## Next Phase

Phase 2 will implement the identity directory structure, including:

- Users
- Groups
- Departments
- Administrative groups
- Service accounts
- Naming conventions
