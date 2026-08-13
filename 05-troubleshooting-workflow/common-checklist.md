# Network Troubleshooting Checklist

## Overview

The following checklist provides a repeatable process for investigating common network connectivity issues. Not every step applies to every situation, but following a consistent workflow helps reduce troubleshooting time.

---

## Initial Assessment

- [ ] What is the reported problem?
- [ ] Is the issue reproducible?
- [ ] Is one user affected or multiple users?
- [ ] Did the issue begin after a recent change?
- [ ] Has the service worked previously?

---

## Client Configuration

- [ ] Verify IP address
- [ ] Verify subnet mask
- [ ] Verify default gateway
- [ ] Verify DNS server configuration
- [ ] Verify network adapter status

---

## Connectivity

- [ ] Ping the default gateway
- [ ] Ping another local device
- [ ] Test Internet connectivity (if applicable)
- [ ] Perform a traceroute if routing issues are suspected

---

## DNS

- [ ] Verify hostname resolution
- [ ] Query an alternate DNS server
- [ ] Check for stale DNS cache entries

---

## Application Connectivity

- [ ] Test the required TCP port
- [ ] Verify the application is listening
- [ ] Confirm firewall rules
- [ ] Verify certificates if HTTPS is used

---

## Server Verification

- [ ] Verify the service is running
- [ ] Check listening ports
- [ ] Review recent log entries
- [ ] Verify resource utilization

---

## Resolution

- [ ] Confirm the issue is resolved
- [ ] Document the root cause
- [ ] Record corrective actions
- [ ] Identify opportunities to prevent recurrence

---

## Notes

Not every troubleshooting step is required for every incident. The checklist should be adapted based on the symptoms and the environment being investigated.
