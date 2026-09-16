# Project 5 — Security Validation

**Status:** Complete

## Objective

Validate the security controls implemented during the previous router security projects.

Testing focused on network isolation, Internet connectivity, firewall behavior, inbound exposure, and service discovery.

---

# Validation Methodology

Testing was performed from the Ubuntu workstation while connected to the private lab network.

The following areas were reviewed:

- Network connectivity
- Internet access
- Upstream network isolation
- Firewall behavior
- Port forwarding
- DMZ configuration
- Open services
- Inbound exposure
- Network segmentation

---

# 1. Gateway Verification

The Ubuntu workstation's routing configuration was reviewed.

```bash
ip route
```

### Result

The workstation uses the Firewall Router as its default gateway.

**Result:** ✅ Pass

---

# 2. Internet Connectivity

Public Internet connectivity was tested.

```bash
ping -c 4 8.8.8.8
```

### Result

The lab workstation successfully maintained Internet connectivity.

**Result:** ✅ Pass

DNS/external connectivity was also tested:

```bash
ping -c 4 google.com
```

**Result:** ✅ Pass

---

# 3. Upstream Network Isolation

A host on the upstream home network was tested from the lab workstation.

The purpose was to determine whether the lab could communicate with hosts outside the lab network.

Access to the tested upstream host was blocked.

**Result:** 🚫 Blocked

---

# 4. Nmap Validation

Nmap was used from the Ubuntu workstation to identify the state of common TCP services on the tested upstream host.

```text
22/tcp   filtered
53/tcp   filtered
80/tcp   filtered
443/tcp  filtered
```

### Interpretation

The tested ports were reported as **filtered**.

This indicates that Nmap could not establish the expected response needed to determine the ports as open or closed.

The result is consistent with the configured firewall policy restricting traffic from the lab toward the tested upstream private host.

---

# 5. Firewall Exposure Review

The router configuration was reviewed for unnecessary inbound exposure.

```text
Port forwarding:        None
DMZ:                    Disabled
Unnecessary ports:      None intentionally opened
Firewall:               Enabled
NAT:                    Enabled
```

**Result:** ✅ Pass

---

# 6. Validation Summary

| Test                                | Result       |
| ----------------------------------- | ------------ |
| Lab uses Firewall Router as gateway | ✅ Pass      |
| Lab → Internet                      | ✅ Pass      |
| Lab → Upstream gateway              | ⚠️ Reachable |
| Lab → Tested upstream host          | 🚫 Blocked   |
| TCP 22                              | Filtered     |
| TCP 53                              | Filtered     |
| TCP 80                              | Filtered     |
| TCP 443                             | Filtered     |
| Unsolicited inbound access          | 🚫 Blocked   |
| Port forwarding                     | None         |
| DMZ                                 | Disabled     |

---

# Security Finding

Testing demonstrated that the lab maintained Internet connectivity while access from the lab to the tested upstream private host was restricted.

The upstream gateway remained reachable. This was evaluated separately because it is the next-hop gateway and does not by itself demonstrate access to other hosts on the upstream network.

The Nmap results provided additional evidence that services on the tested upstream host were not directly reachable from the lab workstation.

---

# Security Validation Limitations

The testing performed in this project represents validation of the configured lab environment and tested hosts.

A filtered Nmap result does not prove that every host or service on the upstream network is inaccessible.

Future validation can expand testing to:

- Additional authorized test hosts
- Additional protocols
- IPv6
- Internal lab hosts
- Firewall logging
- Inbound connection testing
- Service enumeration within the lab

---

# Lessons Learned

This project demonstrated practical experience with:

- Network security validation
- Firewall testing
- Network segmentation
- Nmap
- Service discovery
- Connectivity testing
- Interpreting filtered ports
- Reviewing inbound exposure
- Documenting security findings

---

# Final Result

The Firewall Router security configuration was validated through configuration review and controlled network testing.

The lab maintained Internet connectivity while restricting access to the tested upstream private host.

**Project Status:** ✅ Complete
