# Network Troubleshooting Foundations

## 1. Overview

This repository contains practical networking notes, diagnostic command examples, packet analysis exercises, and troubleshooting workflows developed through independent study and testing. Its emphasis is on **systematic investigation, interpreting results, and identifying root causes**, rather than simply collecting commands.

The material supports Windows and Linux systems administration, infrastructure and application support, and defensive cybersecurity operations.

## 2. Technologies and Tools

- **Platforms:** Rocky Linux (RHEL-compatible) and Windows 11 Pro
- **Linux:** `ip`, `nmcli`, `ping`, `traceroute`, `mtr`, `dig`, `nslookup`, `ss`, `curl`, `wget`, `tcpdump`
- **Windows:** `ipconfig`, `Test-NetConnection`, `Resolve-DnsName`, `Get-NetTCPConnection`, `Get-NetIPConfiguration`, `netsh`
- **Packet analysis:** Wireshark and TCP/IP protocol inspection

## 3. Documentation

### Network Fundamentals

1. [OSI Model](01-network-fundamentals/osi-model.md)
2. [TCP/IP Basics](01-network-fundamentals/tcp-ip-basics.md)
3. [Common Ports](01-network-fundamentals/common-ports.md)

### Linux Troubleshooting Tools

1. [Ping and Traceroute](02-linux-tools/ping-traceroute.md)
2. [dig and nslookup](02-linux-tools/dig-nslookup.md)
3. [Socket Statistics (ss)](02-linux-tools/ss.md)
4. [curl and wget](02-linux-tools/curl-wget.md)
5. [tcpdump Basics](02-linux-tools/tcpdump-basics.md)
6. [DHCP Client](02-linux-tools/dhcp-client.md)

### Windows Troubleshooting Tools

1. [Test-NetConnection](03-windows-tools/test-netconnection.md)
2. [Resolve-DnsName](03-windows-tools/resolve-dnsname.md)
3. [Get-NetTCPConnection](03-windows-tools/get-nettcpconnection.md)
4. [netsh Examples](03-windows-tools/netsh-examples.md)
5. [DHCP and ipconfig](03-windows-tools/dhcp-ipconfig.md)

### Packet Analysis

1. [Wireshark Basics](04-packet-analysis/wireshark-basics.md)
2. [Reading Packets](04-packet-analysis/reading-packets.md)

### Troubleshooting Workflow

1. [Layered Troubleshooting](05-troubleshooting-workflow/layered-troubleshooting.md)
2. [Common Troubleshooting Checklist](05-troubleshooting-workflow/common-checklist.md)

Screenshots are included in the relevant guides; supporting image files are organized under `images/`.

## 4. Lab Environment and Scope

Examples use isolated lab environments, including:

- **Rocky Linux:** A RHEL-compatible system for Linux network diagnostics.
- **Windows 11 Pro:** A domain-joined client in a hybrid Active Directory–Microsoft Entra environment for Windows networking tests.

The troubleshooting approach uses the OSI model to progressively narrow potential causes. Typical activities include checking connectivity, DNS, routing, listening ports, service availability, and packet captures, then documenting findings.

The repository focuses on **observation, validation, and defensive troubleshooting**. It does not cover exploitation, penetration testing, or aggressive or unauthorized scanning. Commands and procedures should be assessed for safety before use in production environments.

## 5. Project Status

The network fundamentals, Linux and Windows tools, packet analysis, and troubleshooting workflow guides are available. The repository remains under development.

Three scenario files under `06-real-world-scenarios/` are placeholders, **not completed case studies**:

- DNS resolution failure
- Service not listening
- API timeout

These will be linked from the documentation index when substantive walkthroughs are added.

## 6. References and Learning Resources

- **ISO/IEC 7498-1:** OSI Reference Model
- [Cloudflare — What Is the OSI Model?](https://www.cloudflare.com/learning/network-layer/what-is-the-osi-model/)
- [Microsoft Learn — Windows Server Networking](https://learn.microsoft.com/en-us/windows-server/networking/)
- [Linux Manual Pages](https://man7.org/linux/man-pages/)

Additional references are cited in individual guides where applicable.
