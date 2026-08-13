# DNS Resolution Failure

## Overview

This scenario demonstrates a structured approach to diagnosing a DNS resolution problem using standard Windows and Linux networking tools.

---

## Scenario

A user reports that a website cannot be reached using its hostname.

```
https://intranet.example.com
```

However, the service is known to be available.

---

## Symptoms

- Browser cannot locate the website.
- `ping intranet.example.com` fails.
- Access by IP address succeeds.

---

## Investigation

### Verify IP Configuration

Windows

```powershell
ipconfig /all
```

Linux

```bash
ip addr
ip route
```

---

### Test DNS Resolution

Windows

```powershell
Resolve-DnsName intranet.example.com

nslookup intranet.example.com
```

Linux

```bash
dig intranet.example.com

nslookup intranet.example.com
```

---

### Compare Results

Verify:

- Configured DNS server
- Returned IP address
- Response time
- Error messages

---

## Findings

Example:

- DNS server was incorrectly configured.
- Name resolution failed.
- Direct communication by IP address was successful.

---

## Resolution

Update the DNS server configuration and verify that the hostname resolves correctly.

---

## Lessons Learned

- DNS failures often appear to users as application failures.
- Testing by IP address helps determine whether DNS is involved.
- Verify DNS before investigating application services.

---

## Screenshots

*(Insert screenshots from Windows and Rocky Linux lab.)*
