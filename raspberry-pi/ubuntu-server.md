# Ubuntu Server on Raspberry Pi

## Overview

Ubuntu Server was installed on the Raspberry Pi 3A+ to provide a lightweight Linux server for the physical Home SOC lab.

The system is managed primarily through the terminal and SSH rather than a graphical desktop environment.

## Environment

| Component        | Configuration    |
| ---------------- | ---------------- |
| Hardware         | Raspberry Pi 3A+ |
| Operating System | Ubuntu Server    |
| Architecture     | ARM              |
| Storage          | microSD          |
| Network          | Wi-Fi            |
| Router           | Opal GL-SFT1200  |
| Administration   | SSH              |

## Installation

Ubuntu Server was installed using Raspberry Pi Imager.

The imaging process configured:

- Ubuntu Server
- Initial user account
- Hostname
- Wi-Fi networking
- SSH

The microSD card was then inserted into the Raspberry Pi and the system was powered on.

## First Boot

During the first boot, Ubuntu Server performed its initialization process.

Cloud-init was observed running during startup, confirming that the Ubuntu installation was progressing normally.

This was an important troubleshooting checkpoint because it established that the problem was not a complete operating-system boot failure.

## Network Configuration

Ubuntu Server uses Netplan for network configuration.

Network configuration files can be found under:

```bash
/etc/netplan/
```

The configuration can be inspected with:

```bash
ls /etc/netplan/
```

A configuration file can then be viewed with:

```bash
sudo cat /etc/netplan/<configuration-file>.yaml
```

Sensitive values should never be published.

For example:

```yaml
network:
  version: 2
  wifis:
    wlan0:
      access-points:
        "<LAB_SSID>":
          password: "<REDACTED>"
      dhcp4: true
```

The exact configuration can vary depending on the Ubuntu version and installation process.

## Applying Configuration

After making a Netplan configuration change, the configuration can be applied with:

```bash
sudo netplan apply
```

For interactive testing, Netplan also provides:

```bash
sudo netplan try
```

## Network Verification

The following commands are useful for verifying connectivity.

### View Interfaces

```bash
ip a
```

This can be used to determine whether the wireless interface is present and whether it has an IP address.

### View Routing

```bash
ip route
```

This shows the system's routing table and default gateway.

### View Network Status

```bash
networkctl
```

This provides information about the state of network interfaces.

### Test the Local Gateway

```bash
ping -c 4 <ROUTER_IP>
```

### Test Internet Connectivity

```bash
ping -c 4 8.8.8.8
```

### Test DNS Resolution

```bash
ping -c 4 google.com
```

These tests help separate different network problems:

```text
Router test
    ↓
Local network connectivity

8.8.8.8 test
    ↓
Internet routing/connectivity

google.com test
    ↓
DNS resolution
```

## SSH Administration

SSH was enabled during the initial Raspberry Pi configuration.

A remote connection can be made using:

```bash
ssh <USERNAME>@<PI_IP>
```

Private IP addresses and usernames should be replaced with appropriate values and should not be published if they reveal sensitive information about the home network.

## Security Practices

The Raspberry Pi is part of a private lab environment.

Security practices include:

- Using SSH instead of exposing unnecessary services
- Keeping credentials out of Git
- Avoiding publication of private network information
- Using a dedicated lab network where appropriate
- Documenting configuration changes
- Troubleshooting connectivity before modifying unrelated system components
