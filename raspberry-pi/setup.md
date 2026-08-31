# Raspberry Pi Setup

## Overview

This document covers the initial physical and imaging setup of the Raspberry Pi 3A+ for the Home SOC physical lab.

The objective was to install Ubuntu Server and configure the Raspberry Pi to operate as a network-connected Linux server.

## Hardware

- Raspberry Pi 3A+
- microSD card
- Power supply
- Wireless network
- Opal GL-SFT1200 router

Because the Raspberry Pi 3A+ does not have an Ethernet port, the initial network configuration was performed using Wi-Fi.

## Operating System

The Raspberry Pi was configured with:

- **Operating System:** Ubuntu Server
- **Architecture:** ARM
- **Boot Media:** microSD card

## Raspberry Pi Imager

Ubuntu Server was written to the microSD card using Raspberry Pi Imager.

The general process was:

1. Open Raspberry Pi Imager.
2. Select the Raspberry Pi device.
3. Select Ubuntu Server as the operating system.
4. Select the microSD card.
5. Configure the operating system settings.
6. Configure wireless networking.
7. Enable SSH for remote administration.
8. Write the operating system to the microSD card.
9. Safely eject the microSD card.
10. Insert the card into the Raspberry Pi.
11. Power on the Raspberry Pi.

## Initial Configuration

During imaging, the following types of settings were configured:

### Hostname

A hostname was assigned to identify the Raspberry Pi on the lab network.

```text
<HOSTNAME>
```

### User Account

A local Ubuntu user account was configured for administration.

### Wi-Fi

The Raspberry Pi was configured to connect to the lab's wireless network.

Sensitive information is intentionally omitted:

```text
SSID: <LAB_SSID>
Password/PSK: <REDACTED>
```

### SSH

SSH was enabled to allow remote administration of the Ubuntu Server system.

The SSH service allows the server to be managed without requiring a monitor, keyboard, or mouse connected directly to the Pi.

## First Boot

After the microSD card was inserted and the Pi was powered on, Ubuntu Server began its first boot process.

Cloud-init also ran during the initial startup process.

This confirmed that the operating system was successfully booting and progressing through its initialization process.

## Initial Verification

After booting, the system was checked to determine whether:

- Ubuntu Server successfully started
- The network interface was available
- Wi-Fi connectivity was working
- The system received an IP address
- SSH could be used for remote administration

Example commands used for network verification included:

```bash
ip a
```

```bash
ip route
```

```bash
networkctl
```

## Security Notes

No real credentials or private network information should be committed to GitHub.

Use placeholders in documentation:

```text
<LAB_SSID>
<PRIVATE_IP>
<ROUTER_IP>
<PSK>
```

Never commit:

- Wi-Fi passwords
- SSH private keys
- Authentication tokens
- API keys
- Sensitive IP information
