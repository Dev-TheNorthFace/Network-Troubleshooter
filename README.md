# Network Troubleshooter --- By NORTH

**Network Troubleshooter --- By NORTH** is a Windows network diagnostic
and repair utility designed to automatically identify where an Internet
connection is failing.

It checks the network path step by step:

``` text
Network Adapter → IPv4 / DHCP → Gateway → DNS → Public IP → Internet HTTP
```

The tool reports the likely problem area and provides appropriate repair
options.

## Main Menu

``` text
[1] Run automatic diagnosis
[2] Network repair menu
[3] Show adapter / IP configuration
[4] Open Windows network settings
[0] Exit
```

## 1. Run Automatic Diagnosis

Runs a complete network diagnostic chain.

### Network Adapter

Checks whether Windows currently has an active network adapter.

If no adapter is active, the tool identifies the problem area as:

``` text
NETWORK ADAPTER / LINK
```

Possible things to check include the Ethernet cable, Wi-Fi connection,
airplane mode, adapter status, and router.

### IPv4 / DHCP

Checks whether the active adapter has a valid IPv4 address.

A missing IPv4 address or an automatic `169.254.x.x` address can
indicate that DHCP did not provide a usable address.

The tool identifies this as:

``` text
IP / DHCP
```

### Default Gateway

Checks whether a default IPv4 gateway is configured and tests whether it
responds.

This helps identify problems between the PC and the local
router/network.

A failed gateway ping is not treated as absolute proof of failure
because some routers block ICMP.

### DNS

Checks the configured DNS servers and attempts to resolve a public
hostname.

If name resolution fails, the tool identifies:

``` text
DNS
```

### Public IP Connectivity

Tests connectivity to a public IP address.

This helps distinguish DNS problems from more general Internet
connectivity problems.

### Internet HTTP Connectivity

Performs an HTTP connectivity test using Microsoft's connectivity-test
endpoint.

If DNS works but the HTTP test fails, possible problem areas include:

``` text
INTERNET ACCESS / ROUTER / ISP / FIREWALL / CAPTIVE PORTAL
```

## 2. Network Repair Menu

Available repair options include:

``` text
[1] Flush DNS cache
[2] Release and renew DHCP lease
[3] Reset Winsock
[4] Reset TCP/IP stack
[5] Disable/enable active network adapters
[6] Run common repairs
[7] Open Windows Network Connections
[0] Back
```

### Flush DNS Cache

Runs the Windows DNS cache flush operation.

Useful when cached DNS information may be stale or incorrect.

### Release and Renew DHCP

Releases the current DHCP lease and requests a new network
configuration.

Useful when the computer has an invalid or outdated IP configuration.

### Reset Winsock

Resets the Windows Winsock catalog.

A Windows restart may be required afterward.

### Reset TCP/IP Stack

Resets Windows TCP/IP networking configuration.

A restart may be required after the operation.

### Restart Active Network Adapters

Temporarily disables and re-enables active network adapters.

This can reinitialize a problematic Ethernet or Wi-Fi connection.

### Run Common Repairs

Runs several common repair operations together:

``` text
Flush DNS
Release DHCP
Renew DHCP
Reset Winsock
```

### Open Windows Network Connections

Opens the classic Windows Network Connections control panel.

## 3. Show Adapter / IP Configuration

Displays useful information for Windows network interfaces, including:

-   Interface name
-   Adapter description
-   IPv4 address
-   Default gateway
-   DNS servers

## 4. Open Windows Network Settings

Opens the Windows network status/settings page directly.

## Administrator Rights

Some repair operations require administrator privileges.

When necessary, Network Troubleshooter can relaunch itself with Windows
administrator elevation.

## Requirements

-   Windows 10 or Windows 11
-   PowerShell / Windows networking components
-   Administrator access for certain repair operations

## Diagnostic Notes

A failed ping does **not always mean that a device or Internet
connection is offline**.

Some routers, servers, and networks intentionally block ICMP traffic.
For this reason, Network Troubleshooter also performs DNS and HTTP
connectivity tests before reporting the likely failure area.

## Recommended Workflow

``` text
1. Launch Network Troubleshooter - By NORTH.exe
2. Select [1] Run automatic diagnosis
3. Read the detected problem area
4. Open [2] Network repair menu if a repair is appropriate
5. Run the relevant repair
6. Restart Windows if requested
7. Run the automatic diagnosis again
```

## Author

Developed by **NORTH**.

## Disclaimer

This software is provided as a Windows network diagnostic and repair
utility.

Network problems can also originate from routers, modems, Internet
service providers, firewalls, VPN software, captive portals, hardware
failures, or external services. Diagnostic results should therefore be
treated as troubleshooting guidance rather than absolute proof of the
underlying cause.
