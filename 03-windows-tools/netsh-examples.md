# Netsh Examples

## Overview

`netsh` (Network Shell) is a Windows command-line utility used to view and configure networking components. Although many tasks are now performed using PowerShell, `netsh` remains useful for troubleshooting and is commonly referenced in Microsoft documentation.

---

## Usage

Use `netsh` to:

- Display network configuration
- Export firewall settings
- Reset the TCP/IP stack
- Reset Winsock
- Display wireless profiles

---

## Common Syntax

### Display Network Interfaces

```cmd
netsh interface show interface
```

### Display IP Configuration

```cmd
netsh interface ip show config
```

### Reset TCP/IP
Resets TCP/IP configuration when troubleshooting persistent network-stack problems

```cmd
netsh int ip reset
```

### Reset Winsock
Resets the Winsock catalog when troubleshooting socket/network communication problems

```cmd
netsh winsock reset
```

### Display Windows Firewall Profiles

```cmd
netsh advfirewall show allprofiles
```

---

## Sample Output

*(Screenshot placeholder)*

---

## Interpretation

Discuss:

- Interface state
- IP configuration
- Wireless profiles
- Firewall profiles

---

## Typical Troubleshooting Scenarios

- Corrupted TCP/IP configuration
- Winsock issues
- Wireless connectivity problems
- Firewall configuration verification

---

## Common Tips

- Some commands require an elevated Command Prompt.
- Restart Windows after performing TCP/IP or Winsock resets.
- Prefer PowerShell cmdlets for new automation, but expect `netsh` in legacy documentation and production environments.

---

## Related Commands

- `ipconfig`
- `Get-NetAdapter`
- `Test-NetConnection`
- `Get-NetIPConfiguration`
