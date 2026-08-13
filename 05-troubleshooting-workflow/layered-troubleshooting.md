# Layered Network Troubleshooting

## Overview

Most network issues can be resolved more efficiently by following a structured troubleshooting process rather than making assumptions or changing multiple variables simultaneously.

This repository uses the OSI model as a practical troubleshooting framework. Although real-world problems often span multiple layers, working methodically from lower layers to higher layers helps isolate the root cause.

---

## A Layered Approach

The following questions provide a logical sequence when investigating connectivity issues.

| Layer | Question | Example Tools |
|------:|----------|---------------|
| Physical | Is the device connected to the network? | `ip link`, `Get-NetAdapter` |
| Data Link | Is the interface operational? Is the correct VLAN being used? | `ip link`, switch diagnostics |
| Network | Does the device have the correct IP configuration? | `ip addr`, `ipconfig`, `ping`, `traceroute` |
| Transport | Is the required TCP or UDP port reachable? | `Test-NetConnection`, `ss`, `netstat` |
| Application | Is the application responding correctly? | `curl`, browser, application logs |

---

## Example Workflow

Suppose a user reports:

> "I can't access the company web application."

A structured investigation might proceed as follows:

1. Verify the network adapter is connected.
2. Confirm the client has a valid IP address.
3. Verify the default gateway.
4. Test connectivity to the gateway.
5. Verify DNS resolution.
6. Test connectivity to TCP port 443.
7. Verify the web application is responding.
8. Review application or server logs if necessary.

Each step narrows the scope of the problem before moving to a higher layer.

---

## Avoid Common Assumptions

Avoid assuming:

- DNS is always the problem.
- A successful `ping` means the application is working.
- Firewall rules are always responsible.
- Restarting services is the first troubleshooting step.

Instead, collect evidence before making configuration changes.

---

## General Principles

- Start with the simplest explanation.
- Verify each assumption.
- Change only one variable at a time.
- Record observations and command output.
- Confirm the issue has been resolved before closing the investigation.

---

## Summary

Following a structured troubleshooting process reduces guesswork, improves consistency, and helps identify the root cause more efficiently.
