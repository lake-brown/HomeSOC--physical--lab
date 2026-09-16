# Project 2 — Firewall & Network Segmentation

**Status:** Complete

## Objective

Configure and validate the Firewall Router as a security boundary between the private HomeSOC-Lab network and the upstream home network.

The goal is to allow necessary Internet connectivity while restricting unnecessary communication with private networks outside the lab.

---

## Intended Traffic Policy

| Traffic            | Policy |
| ------------------ | ------ |
| Lab → Internet     | Allow  |
| Lab → Home Network | Block  |
| Home Network → Lab | Block  |
| Internet → Lab     | Block  |
| Lab → Lab          | Allow  |

---

## Firewall Baseline

The following router security settings were reviewed:

```text
Firewall:               Enabled
NAT:                    Enabled
Port forwarding:        None configured
Manually opened ports:  None configured
DMZ:                    Disabled
Unnecessary services:   Not exposed
```

No TCP or UDP ports were intentionally opened for inbound remote access.

---

## Network Segmentation

A firewall rule was configured to prevent lab devices from initiating connections to private networks reachable through the router's WAN interface.

The rule uses private network address ranges without exposing the actual lab or home network addressing in this repository.

```text
Source Zone:       LAN
Destination Zone:  WAN
Destination:       Private RFC1918 Networks
Action:            DROP
```

### Purpose

The rule provides an additional security boundary between the HomeSOC-Lab and private hosts on the upstream home network.

Public Internet connectivity remains available to the lab.

---

## Validation

Testing was performed from the Ubuntu workstation connected to the lab network.

### Default Gateway

```bash
ip route
```

The workstation was verified to use the Firewall Router as its default gateway.

### Internet Connectivity

External connectivity was tested with:

```bash
ping -c 4 8.8.8.8
```

**Result:** ✅ Internet connectivity maintained.

DNS/external connectivity was also tested:

```bash
ping -c 4 google.com
```

**Result:** ✅ External connectivity maintained.

### Upstream Network

The upstream gateway remained reachable.

**Result:** ⚠️ Gateway reachable.

This does not by itself demonstrate unrestricted access to the upstream network because the gateway is the next-hop router for the Firewall Router.

A separate upstream host was tested.

**Result:** 🚫 Access blocked.

---

## Security Validation Results

| Test                                | Result       |
| ----------------------------------- | ------------ |
| Lab uses Firewall Router as gateway | ✅ Pass      |
| Lab → Internet                      | ✅ Pass      |
| Lab → Upstream gateway              | ⚠️ Reachable |
| Lab → Tested upstream host          | 🚫 Blocked   |
| WAN → Lab unsolicited access        | 🚫 Blocked   |
| Port forwarding                     | ✅ None      |
| DMZ                                 | ✅ Disabled  |
| Unnecessary inbound ports           | ✅ None      |

---

## Result

The Firewall Router successfully provides a security boundary between the lab network and tested hosts on the upstream private network while maintaining Internet connectivity.

**Project Status:** ✅ Complete
