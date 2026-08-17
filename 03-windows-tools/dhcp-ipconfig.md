# DHCP and ipconfig

## Overview

DHCP (Dynamic Host Configuration Protocol) automatically provides network configuration to DHCP-enabled clients. This typically includes an IP address, subnet mask, default gateway, DNS servers, and a lease duration.

In Windows, ipconfig can be used to view the current IP configuration and perform common DHCP and DNS troubleshooting tasks.

## Key concepts

- **Automatic configuration** — DHCP allows clients to obtain network settings without requiring manual IP configuration.
- **Leases** — IP addresses are assigned for a defined period and can be renewed by the client.
- **Centralized management** — DHCP allows administrators to manage address ranges and common network settings from a DHCP server.
- **Address allocation** — The DHCP server manages its available address pool to avoid assigning the same leased address to multiple clients.

## Usage 
`ipconfig` and its DHCP-related options are useful when troubleshooting situations such as:

- **Missing IP configuration** — verify whether the client received an IPv4 address, subnet mask, and default gateway.
- **Incorrect network configuration** — check the assigned address, gateway, DHCP server, and DNS servers.
- **DHCP connectivity problems** — release and renew a lease to test whether the client can obtain configuration from a DHCP server.
- **Network or VLAN changes** — request a new DHCP lease after moving a client to a different network.
- **Expired or problematic leases** — renew the DHCP lease and verify the resulting configuration.
- **DNS troubleshooting** — inspect configured DNS servers or clear the local DNS resolver cache when investigating name-resolution problems.
- **APIPA address (169.254.x.x)** — An automatically assigned address may indicate that the client was unable to obtain an IPv4 configuration from a DHCP server.

## Common Commands

1. **Display basic IP configuration** — Displays basic TCP/IP configuration for network adapters, including the IPv4/IPv6 addresses, subnet mask, and default gateway.  
`ipconfig`

2. **Display detailed IP configuration** — Displays detailed adapter configuration, including MAC address, DHCP status and server, DNS servers, and DHCP lease information.  
`ipconfig /all`

3. **Release a DHCP lease** — Releases the current DHCP-assigned IPv4 configuration for the network adapter.  
`ipconfig /release`

4. **Renew a DHCP lease** — Requests a DHCP lease from the DHCP server and updates the adapter's IPv4 configuration.  
`ipconfig /renew`

5. **Flush the DNS resolver cache** — Clears cached DNS records on the local computer, which can help troubleshoot outdated or incorrect name-resolution results.  
`ipconfig /flushdns`

6. **Register DNS records**— Initiates dynamic registration of the computer's DNS names and IP addresses with its configured DNS server.  
`ipconfig /registerdns`

## Practical Examples

View basic network configuration using `ipconfig` and detailed configuration using `ipconfig /all`.
The Windows client is a VMWare machine from a lab.  

![Viewing configuration using ipconfig](../images/windows/ipconfig.png)  

Release and renew a DHCP lease using `ipconfig /release` and `ipconfig /renew`. 
The `192.168.10.100` address shown below was dynamically assigned by the Windows 
DHCP Server configured in my [AD–Entra Hybrid Identity Lab](https://github.com/tjnieradka/AD-Entra-Lab/blob/main/docs/04-DHCP-Server-Setup.md).

![DHCP lease release and renewal using ipconfig](../images/windows/ipconfig-release-renew.png)


