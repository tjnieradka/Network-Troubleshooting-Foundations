# Resolve-DnsName

## Overview

`Resolve-DnsName` is a PowerShell cmdlet that queries DNS servers and returns detailed information about DNS records. It is the modern PowerShell alternative to `nslookup`.

---

## Usage

Use `Resolve-DnsName` to:

- Verify DNS name resolution
- Troubleshoot DNS-related issues
- Query different DNS record types
- Confirm responses from specific DNS servers

---

## Common Syntax

### Resolve an A Record

```powershell
Resolve-DnsName google.com
```

### Query a Specific DNS Server

```powershell
Resolve-DnsName google.com -Server 8.8.8.8
```

### Query MX Records

```powershell
Resolve-DnsName google.com -Type MX
```

### Reverse Lookup

```powershell
Resolve-DnsName 8.8.8.8
```

---

## Sample Output

*(Screenshot placeholder)*

---

## Interpretation

Discuss:

- Name
- Type
- IPAddress
- TTL
- NameHost

---

## Typical Troubleshooting Scenarios

- DNS server unavailable
- Incorrect DNS records
- Name resolution failures
- Slow DNS responses

---

## Common Tips

- Compare results from multiple DNS servers.
- Verify the configured DNS server before investigating applications.
- Flush the DNS cache if stale records are suspected.

---

## Related Commands

- `nslookup`
- `ipconfig /flushdns`
- `Test-NetConnection`
