# Network Troubleshooting Foundations

Network Troubleshooting Foundations is a collection of practical networking notes, troubleshooting workflows, and diagnostic command examples developed while refreshing and expanding enterprise networking skills.

The repository focuses on systematic network troubleshooting using standard Windows and Linux tools, packet capture fundamentals, and representative real-world troubleshooting scenarios. Rather than serving as a networking reference, the emphasis is on diagnostic methodology, interpreting results, and identifying root causes.

The material is intended to demonstrate knowledge applicable to the following:

- Systems Administration
- Support Engineering
- Cloud & Infrastructure Support
- Application & Platform Support
- Cybersecurity (defensive / operational focus)

---

## Scope

This repository emphasizes the following:

- Structured troubleshooting using the OSI model
- Practical use of standard diagnostic tools
- Interpretation of diagnostic results rather than simply executing commands
- Production-safe investigation techniques
- Clear documentation and reproducible troubleshooting workflows

---

## Lab Environments

The following lab systems are used throughout this repository:

- **Rocky Linux** (RHEL-compatible)  
 A RHEL-compatible Linux distribution representing a typical enterprise or cloud-hosted Linux server.
Tools and concepts demonstrated are generally applicable to modern Linux distributions.

- **Windows 11 Pro** (domain-joined, hybrid AD–Entra environment)  
A domain-joined workstation integrated with a hybrid Active Directory and Microsoft Entra ID environment.
Examples demonstrate Windows networking diagnostics using PowerShell and built-in networking tools commonly available in enterprise environments.

Unless otherwise noted, all demonstrations are performed in isolated lab environments.

## Troubleshooting Methodology

The examples follow a layered troubleshooting approach based on the Open Systems Interconnection (OSI) model.

Rather than memorizing commands, the objective is to develop a repeatable diagnostic process that progressively isolates failures and identifies their underlying causes.

Typical troubleshooting activities include:

- Verifying network connectivity
- Testing DNS resolution
- Validating routing
- Confirming service availability
- Inspecting listening ports
- Capturing and analyzing network traffic
- Interpreting diagnostic output
- Documenting findings and resolution steps

## OSI Model Overview

The **OSI (Open Systems Interconnection) model** provides a conceptual framework for understanding how network communication occurs across layered components. Throughout this repository it serves as a practical troubleshooting guide for narrowing the scope of an issue.

| Layer | Name | Example Focus |
|-----|------|---------------|
| 7 | Application | HTTP, APIs, DNS queries |
| 6 | Presentation | Encoding, encryption |
| 5 | Session | Session establishment |
| 4 | Transport | TCP/UDP, ports |
| 3 | Network | IP addressing, routing |
| 2 | Data Link | MAC addressing, switching |
| 1 | Physical | Cabling, interfaces |

---

## Repository Structure

```text
01-network-fundamentals/
    osi-model.md
    tcp-ip-basics.md
    common-ports.md

02-linux-tools/
    ping-traceroute.md
    dig-nslookup.md
    ss.md
    curl-wget.md
    tcpdump-basics.md
    dhcp-client.md

03-windows-tools/
    test-netconnection.md
    resolve-dnsname.md
    get-nettcpconnection.md
    netsh-examples.md
    dhcp-ipconfig.md

04-packet-analysis/ -- In development
    wireshark-basics.md --- TBA
    reading-packets.md --- TBA

05-troubleshooting-workflow/
    layered-troubleshooting.md
    common-checklist.md

06-real-world-scenarios/   -- In development
    dns-resolution-failure.md --- TBA
    service-not-listening.md --- TBA
    api-timeout.md --- TBA
```

Each section includes:
- Command examples
- Explanation of expected output
- Common failure patterns
- Screenshots where helpful
- Notes on safe usage in production environments

---

## Tools Covered (Non-Exhaustive)

### Linux

- `curl` / `wget`  
- `dig / `nslookup`  
- `ip`    
- `ping`  
- `ss`  
- `tcpdump`  
- `traceroute`
- `mtr`  

### Windows (PowerShell)
- `Test-NetConnection`
- `Resolve-DnsName`
- `Get-NetTCPConnection`
- `Get-NetIPConfiguration`
- `netsh`

---

## Screenshots and Output

Where applicable, screenshots are included to:
- Illustrate command output
- Highlight diagnostic indicators
- Show differences between expected vs faulty states

Screenshots are used to **support explanation**, not as a substitute for analysis.

---

## What This Repository Is *Not*

This repository does **not** include:
- Offensive security techniques
- Exploitation workflows
- Aggressive or unauthorized scanning
- Penetration testing scenarios

All examples are performed in **controlled lab environments** and focus on **observation, validation, and troubleshooting**.

---

## References

The following open and widely accepted references are used throughout this repository:

- ISO/IEC 7498-1 — OSI Reference Model  
- https://www.cloudflare.com/learning/network-layer/what-is-the-osi-model/
- https://learn.microsoft.com/en-us/windows-server/networking/
- https://man7.org/linux/man-pages/
- https://www.geeksforgeeks.org/open-systems-interconnection-model-osi/

Additional references are cited within individual sections where appropriate.

---

## Status

This repository is under active development.  
Content will be expanded incrementally with additional tools, scenarios, and documentation.
