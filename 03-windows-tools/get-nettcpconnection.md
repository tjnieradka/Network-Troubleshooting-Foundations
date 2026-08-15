## Overview

`Get-NetTCPConnection` displays current TCP connections and listening ports on a Windows system. It can be used to examine local and remote addresses and ports, connection states, and the processes associated with TCP connections.

## Usage

Use Get-NetTCPConnection to:

- **Identify listening services** — verify that an application or service is listening on the expected TCP port.
- **View established connections** — identify active TCP sessions between the local computer and remote systems.
- **Investigate unexpected connections** — examine unfamiliar remote addresses, ports, or connection states.
- **Troubleshoot application connectivity** — determine whether a problem involves a service that is not listening on the expected port.
- **Examine TCP connection states** — identify connections in states such as Listen, Established, and TimeWait.
- **Identify owning processes** — use the OwningProcess property with Get-Process to determine which process is associated with a connection.

## Common Commands

1. **Display all TCP connections**  — Displays current TCP connections and listening ports.  
`Get-NetTCPConnection`

2. **Display listening TCP ports** —  Filters the results to TCP endpoints currently in the Listen state.  
`Get-NetTCPConnection -State Listen`

3. **Filter by local port** — Displays TCP connections associated with a specified local port.  
`Get-NetTCPConnection -LocalPort 443`

4. **Filter by remote address** — Displays TCP connections associated with a specified remote IP address.  
`Get-NetTCPConnection -RemoteAddress 192.168.1.25`

5. **Identify processes associated with listening ports** — Displays listening ports with their owning process IDs and resolves the IDs to process names.  
```
Get-NetTCPConnection -State Listen |
Select-Object LocalAddress, LocalPort, State, OwningProcess,
    @{Name="ProcessName";Expression={(Get-Process -Id $_.OwningProcess).ProcessName}} |
Sort-Object LocalPort |
Format-Table -AutoSize
```

## Practical Examples

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
