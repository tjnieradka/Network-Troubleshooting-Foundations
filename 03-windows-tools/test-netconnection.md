# Test-NetConnection

## Overview

`Test-NetConnection` is a PowerShell cmdlet used to verify network connectivity between a Windows client and a remote host. It can test ICMP connectivity, DNS resolution, TCP port availability, and routing information, making it a useful replacement for several traditional networking tools.

---

## Usage

Use `Test-NetConnection` to:

- Verify connectivity to a remote host
- Test whether a specific TCP port is reachable
- Confirm DNS name resolution
- Troubleshoot firewall or routing issues
- Validate connectivity to web servers, database servers, and other network services

---

## Common Syntax

### Basic Connectivity

```powershell
Test-NetConnection google.com
```

### Test a Specific Port

```powershell
Test-NetConnection google.com -Port 443
```

### Display Detailed Information

```powershell
Test-NetConnection google.com -InformationLevel Detailed
```

### Test Remote Desktop

```powershell
Test-NetConnection server01 -Port 3389
```

---

## Sample Output

*(Screenshot or command output placeholder)*

---

## Interpretation

Discuss:

- PingSucceeded
- TcpTestSucceeded
- RemoteAddress
- InterfaceAlias
- SourceAddress

---

## Typical Troubleshooting Scenarios

- HTTPS unavailable
- RDP connection failures
- Firewall blocking TCP ports
- Incorrect DNS resolution
- Routing issues

---

## Common Tips

- ICMP may be blocked while TCP remains available.
- A successful ping does not guarantee an application is responding.
- Testing the required application port is often more useful than relying solely on ping.

---

## Related Commands

- `ping` (Windows and Linux)
- `tracert`
- `Resolve-DnsName`
- `Get-NetTCPConnection`
