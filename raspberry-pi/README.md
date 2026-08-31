# Raspberry Pi — Ubuntu Server

This directory documents the Raspberry Pi portion of my physical Home SOC lab.

The Raspberry Pi 3A+ is configured as an Ubuntu Server system and connected to the lab network over Wi-Fi. This device is used as part of the lab infrastructure for learning Linux administration, networking, system troubleshooting, and cybersecurity operations.

## Hardware

- **Device:** Raspberry Pi 3A+
- **Operating System:** Ubuntu Server
- **Network:** Wi-Fi
- **Network Device:** Opal GL-SFT1200 router

> **Note:** The Raspberry Pi 3A+ does not provide an Ethernet port, so the system was configured for wireless networking.

## Documentation

| Document                              | Description                                        |
| ------------------------------------- | -------------------------------------------------- |
| [Setup](setup.md)                     | Raspberry Pi hardware and initial imaging setup    |
| [Ubuntu Server](ubuntu-server.md)     | Ubuntu Server installation and configuration       |
| [Troubleshooting](troubleshooting.md) | Wi-Fi troubleshooting and root-cause investigation |

## Lab Objectives

The Raspberry Pi portion of the lab is used to practice:

- Linux server administration
- SSH administration
- Network configuration
- Wi-Fi troubleshooting
- Ubuntu Server management
- Network connectivity testing
- Security-focused infrastructure troubleshooting

## Security Considerations

Sensitive information is intentionally excluded from this repository.

Do **not** commit:

- Wi-Fi passwords
- PSKs
- SSH private keys
- API keys
- Authentication tokens
- Public IP addresses
- Private network credentials
- Other personally identifiable network information

Configuration examples should use placeholders such as:

```text
<SSID>
<PSK>
<PRIVATE_IP>
<ROUTER_IP>
```

## Lessons Learned

A major troubleshooting lesson from this setup was that a device can successfully boot the operating system while still failing to establish network connectivity.

The Wi-Fi issue was ultimately traced to the wireless security configuration. Changing the router from **PSK to PSK2** resolved the authentication problem and allowed the Raspberry Pi to connect successfully.
