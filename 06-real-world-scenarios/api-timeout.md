# API Timeout

## Overview

This scenario demonstrates a structured approach to investigating an API connection timeout.

---

## Scenario

A client application reports:

```
Request timed out.
```

The application cannot retrieve data from a REST API.

---

## Symptoms

- Browser functions normally.
- API request fails.
- Connection eventually times out.

---

## Investigation

### Verify DNS

```powershell
Resolve-DnsName api.example.com
```

---

### Verify Connectivity

```powershell
Test-NetConnection api.example.com -Port 443
```

---

### Test HTTP Response

Linux

```bash
curl -I https://api.example.com
```

Windows

```powershell
Invoke-WebRequest https://api.example.com
```

---

### Capture Traffic (Optional)

Capture traffic using tcpdump or Wireshark to verify that packets are exchanged.

---

## Findings

Example:

TCP connectivity was successful.

The API returned HTTP 504 Gateway Timeout.

---

## Resolution

The issue originated on the application server rather than the client network.

---

## Lessons Learned

Timeouts may occur at multiple layers.

A structured investigation helps determine whether the issue is related to networking, transport, or the application itself.

---

## Screenshots

*(Insert screenshots of command output and HTTP responses.)*
