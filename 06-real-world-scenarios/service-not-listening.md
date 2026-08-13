# Service Not Listening

## Overview

This scenario demonstrates how to verify whether a network service is actively listening on the expected TCP port.

---

## Scenario

Users report that HTTPS is unavailable.

The server responds to ping but the website does not load.

---

## Symptoms

- Ping succeeds.
- Browser reports connection failure.
- TCP port 443 cannot be reached.

---

## Investigation

### Verify Port Connectivity

Windows

```powershell
Test-NetConnection server01 -Port 443
```

Linux

```bash
curl https://server01

ss -tulpn
```

---

### Verify Listening Ports

Linux

```bash
ss -tulpn
```

Windows

```powershell
Get-NetTCPConnection -State Listen
```

---

### Verify Firewall

Review Windows Defender Firewall or firewalld configuration.

---

## Findings

Example:

The web service had stopped and was no longer listening on TCP port 443.

---

## Resolution

Restart the service and verify that the application is again listening on the expected port.

---

## Lessons Learned

A successful ping confirms only basic network connectivity.

Application availability should always be verified by testing the required TCP or UDP port.

---

## Screenshots

*(Insert screenshots demonstrating listening ports before and after the service is started.)*
