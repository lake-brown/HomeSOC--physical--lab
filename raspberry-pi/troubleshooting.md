# Raspberry Pi Wi-Fi Troubleshooting

## Incident Summary

During the initial setup of Ubuntu Server on the Raspberry Pi 3A+, the system successfully booted but could not establish a working Wi-Fi connection.

The Raspberry Pi does not have an Ethernet port, so Wi-Fi was required for network connectivity.

The issue was ultimately resolved by changing the router's wireless security configuration from **PSK to PSK2**.

## Environment

- **Device:** Raspberry Pi 3A+
- **Operating System:** Ubuntu Server
- **Network:** Wi-Fi
- **Router:** Opal GL-SFT1200

Sensitive network information has been intentionally removed.

## Initial Symptoms

The Raspberry Pi:

- Powered on successfully
- Booted Ubuntu Server
- Ran the Ubuntu initialization process
- Was not successfully connecting to the wireless network

This indicated that the problem was more likely related to networking than to the Raspberry Pi's ability to boot Ubuntu.

## Troubleshooting Approach

The troubleshooting process followed a layered approach:

```text
Hardware
   ↓
Operating System
   ↓
Network Interface
   ↓
Wi-Fi Configuration
   ↓
Authentication
   ↓
IP Address
   ↓
Routing
   ↓
Internet Connectivity
```

This prevented unrelated components from being changed unnecessarily.

## Step 1 — Verify the System Booted

Ubuntu Server successfully started and cloud-init was observed running during initialization.

This established that:

```text
Power
  ↓
Raspberry Pi
  ↓
microSD
  ↓
Ubuntu Server
```

was functioning.

### Finding

The problem was unlikely to be a complete operating-system or boot failure.

## Step 2 — Check Network Interfaces

The network interfaces were examined using:

```bash
ip a
```

The purpose was to determine whether the wireless interface was present and whether it had received an IP address.

Additional network information could be examined with:

```bash
networkctl
```

and:

```bash
ip route
```

## Step 3 — Check Wi-Fi Configuration

Ubuntu Server uses Netplan for network configuration.

The Netplan directory was examined with:

```bash
ls /etc/netplan/
```

The applicable configuration could then be inspected with:

```bash
sudo cat /etc/netplan/<configuration-file>.yaml
```

The configuration was checked for the expected:

- Wireless interface
- SSID
- Authentication information
- DHCP configuration

Credentials are intentionally excluded from this documentation.

## Step 4 — Investigate Router Security

The router's wireless security configuration was reviewed.

The Pi and router needed to use compatible wireless authentication settings.

The original configuration used:

```text
PSK
```

The Raspberry Pi was unable to successfully authenticate to the wireless network using this configuration.

## Root Cause

The issue was a **wireless authentication/security-mode mismatch** between the Raspberry Pi's Wi-Fi configuration and the router's security configuration.

The router's original **PSK** mode was not working correctly with the Pi's Ubuntu Server wireless setup.

## Resolution

The router's wireless security mode was changed:

```text
PSK
 ↓
PSK2
```

After making this change, the Raspberry Pi successfully connected to the wireless network.

## Validation

After the security configuration was corrected, network connectivity could be verified using commands such as:

```bash
ip a
```

to check for an assigned IP address.

The routing table could be checked with:

```bash
ip route
```

Local connectivity could be tested with:

```bash
ping -c 4 <ROUTER_IP>
```

Internet connectivity could then be tested with:

```bash
ping -c 4 8.8.8.8
```

DNS resolution could be tested with:

```bash
ping -c 4 google.com
```

## Result

The Raspberry Pi successfully connected to the lab's Wi-Fi network after changing the router's wireless security mode from **PSK to PSK2**.

## Troubleshooting Lessons

### 1. Don't assume the OS is broken

The Pi was successfully booting Ubuntu Server. This allowed the investigation to move up the stack toward networking.

### 2. Check each layer

A structured approach makes troubleshooting easier:

```text
Physical
   ↓
OS
   ↓
Interface
   ↓
Configuration
   ↓
Authentication
   ↓
IP
   ↓
Routing
   ↓
DNS
```

### 3. Authentication problems can look like general connectivity problems

A device may be powered on and running normally while still being unable to communicate because wireless authentication is failing.

### 4. Change one variable at a time

Changing the router from PSK to PSK2 provided a clear test of the wireless security configuration.

Once connectivity worked, the configuration change provided strong evidence that the authentication mode was the cause.

## Security Considerations

This repository intentionally does not contain:

- Wi-Fi passwords
- PSKs
- SSH private keys
- API keys
- Authentication tokens
- Public IP addresses
- Sensitive private IP information
- Other credentials

Use placeholders such as:

```text
<LAB_SSID>
<PSK>
<PRIVATE_IP>
<ROUTER_IP>
```

when documenting the environment publicly.
