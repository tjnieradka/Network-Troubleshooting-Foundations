# Network Troubleshooting Foundations

This repository documents hands-on network troubleshooting concepts, tools, and scenarios based on the **OSI model**, with practical examples using **Linux** and **Windows** systems.  

The focus is on **diagnostic thinking, safe investigation techniques, and root-cause analysis**, rather than offensive security or penetration testing.

The material is intended to support learning and demonstration of skills relevant to:
- Systems Administration
- Support Engineering
- Cloud & Infrastructure Support
- Application & Platform Support
- Cybersecurity (defensive / operational focus)

---

## Scope and Philosophy

This repository emphasizes:
- Structured troubleshooting using the **OSI model**
- Practical use of **standard diagnostic tools**
- Interpretation of results (not just command execution)
- Production-safe investigation techniques
- Clear documentation and reproducibility

The examples intentionally mirror **real-world enterprise environments**, rather than isolated or artificial lab setups.

---

## Lab Environments

The following lab systems are used throughout this repository:

- **Rocky Linux** (RHEL-compatible)  
  Used to represent a typical enterprise or cloud-hosted Linux system.  
  Tools demonstrated are applicable to most modern Linux distributions.

- **Windows 11 Pro** (domain-joined, hybrid AD–Entra environment)  
  Used to demonstrate Windows networking and PowerShell-based diagnostics in an enterprise client context.

> Network diagnostics are intentionally performed across different system roles to reflect real-world environments where clients, servers, and services operate in different trust and identity contexts.

---

## OSI Model Overview (Brief)

The **OSI (Open Systems Interconnection) model** provides a conceptual framework for understanding how network communication occurs across layered components.

| Layer | Name | Example Focus |
|-----|------|---------------|
| 7 | Application | HTTP, APIs, DNS queries |
| 6 | Presentation | Encoding, encryption |
| 5 | Session | Session establishment |
| 4 | Transport | TCP/UDP, ports |
| 3 | Network | IP addressing, routing |
| 2 | Data Link | MAC addressing, switching |
| 1 | Physical | Cabling, interfaces |

In practice, the OSI model is used here as a **troubleshooting heuristic**, helping narrow down where failures are likely occurring.

---

## Repository Structure
<PRE>
network-troubleshooting-foundations/
├── README.md
├── osi-model/
│ ├── osi-overview.md
│ └── osi-troubleshooting-examples.md
├── linux-tools/
│ ├── ping-traceroute.md
│ ├── ss-netstat.md
│ ├── dig-nslookup.md
│ ├── curl-wget.md
│ ├── tcpdump-basics.md
│ └── firewall-considerations.md
├── windows-powershell/
│ ├── test-netconnection.md
│ ├── resolve-dnsname.md
│ ├── get-nettcpconnection.md
│ ├── netsh-examples.md
│ └── common-scenarios.md
├── wireshark/
│ ├── capture-basics.md
│ └── reading-packets.md
└── real-world-scenarios/
├── api-timeout.md
├── dns-resolution-failure.md
└── service-not-listening.md
</PRE>

Each section includes:
- Command examples
- Explanation of expected output
- Common failure patterns
- Screenshots where helpful
- Notes on safe usage in production environments

---

## Tools Covered (Non-Exhaustive)

### Linux
- `ip`
- `ss`
- `ping`
- `traceroute`
- `dig` / `nslookup`
- `curl` / `wget`
- `tcpdump`
- `nmap` (limited to safe discovery usage)
- `firewalld` / `nftables` considerations

### Windows (PowerShell)
- `Test-NetConnection`
- `Resolve-DnsName`
- `Get-NetTCPConnection`
- `Get-NetIPConfiguration`
- `netsh`
- Windows Defender Firewall tools

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
- Unauthorized scanning
- Penetration testing scenarios

All examples are performed in **controlled lab environments** and focus on **observation, validation, and troubleshooting**.

---

## References

The following open and widely accepted references are used throughout this repository:

- ISO/IEC 7498-1 — OSI Reference Model  
- https://en.wikipedia.org/wiki/OSI_model
- https://www.cloudflare.com/learning/network-layer/what-is-the-osi-model/
- https://learn.microsoft.com/en-us/windows-server/networking/
- https://man7.org/linux/man-pages/
- https://www.geeksforgeeks.org/open-systems-interconnection-model-osi/

Additional references are cited within individual sections where appropriate.

---

## Status

This repository is under active development.  
Content will be expanded incrementally with additional tools, scenarios, and documentation.
