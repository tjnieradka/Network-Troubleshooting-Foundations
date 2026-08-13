# Get-NetTCPConnection

## Overview

`Get-NetTCPConnection` displays active TCP connections and listening ports on a Windows system. It is useful for verifying whether applications are accepting connections and identifying established sessions.

---

## Usage

Use `Get-NetTCPConnection` to:

- Verify that services are listening
- View active TCP connections
- Identify local and remote ports
- Troubleshoot connectivity issues

---

## Common Syntax

### Display All TCP Connections

```powershell
Get-NetTCPConnection
```

### Display Listening Ports

```powershell
Get-NetTCPConnection -State Listen
```

### Filter by Local Port

```powershell
Get-NetTCPConnection -LocalPort 443
```

### Filter by Remote Address

```powershell
Get-NetTCPConnection -RemoteAddress 192.168.1.25
```

---

## Sample Output

*(Screenshot placeholder)*

---

## Interpretation

Discuss:

- LocalAddress
- LocalPort
- RemoteAddress
- RemotePort
- State
- OwningProcess

---

## Typical Troubleshooting Scenarios

- Service not listening
- Incorrect listening port
- Unexpected connections
- Connection states (LISTEN, ESTABLISHED, TIME_WAIT)

---

## Common Tips

- Combine with `Get-Process` to identify applications.
- Verify the expected service is listening before investigating firewall issues.

---

## Related Commands

- `netstat -ano`
- `Test-NetConnection`
- `Get-Process`
