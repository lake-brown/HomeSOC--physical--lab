# Project 1 — Wireless Security

**Status:** Complete

## Objective

Establish a dedicated and secured wireless network for the HomeSOC-Lab while keeping lab devices separate from the normal home wireless network.

---

## Environment

The Firewall Router provides the dedicated wireless network used by the cybersecurity lab.

Lab systems connect to the Firewall Router rather than directly connecting to the home wireless network.

---

## Security Controls

The following wireless security controls were configured or reviewed:

- Dedicated lab SSID
- WPA2/WPA3 wireless security
- Strong unique wireless password
- 2.4 GHz wireless support for Raspberry Pi connectivity
- WPS disabled where available
- Lab devices separated from the home wireless network

---

## Configuration

The wireless network was configured specifically for authorized HomeSOC-Lab systems.

The Raspberry Pi required 2.4 GHz wireless compatibility for connectivity.

During setup, the wireless security configuration was adjusted to resolve Raspberry Pi connectivity issues.

---

## Validation

Wireless connectivity was tested from the lab systems.

Validation confirmed:

- Raspberry Pi could connect to the lab wireless network
- Ubuntu workstation could connect to the lab wireless network
- Lab systems received network connectivity
- Lab devices were connected through the dedicated lab network rather than the normal home wireless network

---

## Security Considerations

The following information is intentionally excluded from this repository:

- Wireless password
- Actual SSID if considered sensitive
- IP addresses
- MAC addresses
- Router credentials
- Personal network information

---

## Result

The dedicated wireless network provides connectivity for authorized HomeSOC-Lab systems while maintaining separation from the normal home wireless environment.

**Project Status:** ✅ Complete
