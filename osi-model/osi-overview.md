# OSI Model Overview (Troubleshooting-Oriented)

The **OSI (Open Systems Interconnection) model** is a conceptual framework that describes how data moves from one system to another across a network.  
While modern networks are often described using the TCP/IP model, the OSI model remains extremely useful as a **troubleshooting and reasoning tool**.

In this repository, the OSI model is used primarily to:
- Structure network troubleshooting
- Narrow down where a failure is likely occurring
- Choose appropriate diagnostic tools
- Avoid guessing by following a layered approach

---

## Why the OSI Model Is Useful for Troubleshooting

When a network issue occurs, symptoms are often visible at the application level (e.g., a website not loading), but the root cause may exist at a lower layer (e.g., DNS, routing, or firewall rules).

The OSI model provides a systematic way to ask the following:
- *Is this a physical or connectivity problem?*
- *Is name resolution working?*
- *Are ports reachable?*
- *Is the application responding correctly once reached?*

Rather than presenting memorized protocols per layer, this repository uses the OSI model as **a structured troubleshooting framework**.

---

## OSI Layers (High-Level Summary)

| Layer | Name | Practical Focus |
|-----|------|-----------------|
| 7 | Application | User-facing services, APIs, DNS, HTTP |
| 6 | Presentation | Encryption, encoding, TLS |
| 5 | Session | Session establishment and management |
| 4 | Transport | Ports, TCP/UDP connectivity |
| 3 | Network | IP addressing and routing |
| 2 | Data Link | Local network delivery (Ethernet) |
| 1 | Physical | Physical interfaces and signals |

In real-world troubleshooting, multiple layers are often involved at once. Tools commonly span more than one layer.

---

## Encapsulation and De-Encapsulation (Conceptual)

When data is sent from one device to another:
1. Application data is generated at Layer 7.
2. Each lower layer **encapsulates** the data with its own header.
3. The final bit stream is transmitted over the physical medium.
4. The receiving system **de-encapsulates** the data layer by layer.

Understanding encapsulation helps explain the following:
- Why packet captures show multiple headers.
- Why transport means (TCP/UDP) matter for applications.
- Why tools at different layers expose different information.

A visual illustration of this process is commonly shown in OSI encapsulation diagrams referenced from open educational sources.  
One such example is available from GeeksforGeeks:  https://www.geeksforgeeks.org/open-systems-interconnection-model-osi/

---

## OSI Layers from a Troubleshooting Perspective

### Layer 1 – Physical
Focus:
- Is the interface up?
- Is there a link?
- Is the VM or NIC connected?

Examples:
- Interface state
- Link speed
- Virtual network adapter configuration

---

### Layer 2 – Data Link
Focus:
- Can frames be delivered on the local network?
- Is the system on the correct network segment?

Examples:
- MAC addressing
- Local switching behavior

---

### Layer 3 – Network
Focus:
- Can the system reach another IP address?
- Is routing functioning as expected?

Common checks:
- IP configuration
- ICMP reachability
- Traceroute behavior

---

### Layer 4 – Transport
Focus:
- Are required ports reachable?
- Is the service listening?
- Is the connection state healthy?

Examples:
- TCP vs UDP behavior
- Port-level connectivity
- Connection states

---

### Layer 5 – Session
Focus:
- Is the session established and maintained?
- Are connections being dropped or reset?

Show up indirectly through:
- Connection persistence
- Timeouts
- Authentication-related session behavior

---

### Layer 6 – Presentation
Focus:
- Is encryption or data formatting causing issues?

Examples:
- TLS negotiation failures
- Certificate problems
- Protocol mismatches

---

### Layer 7 – Application
Focus:
- Is the service responding correctly?
- Is the request valid?
- Is the application returning errors?

Examples:
- HTTP status codes
- API responses
- DNS query results

---

## Using the OSI Model in This Repository

Each tool and scenario in this repository is mapped (implicitly or explicitly) to one or more OSI layers.  
The goal is not to force an exact classification, but to show how **layered thinking improves troubleshooting efficiency**.

Examples:
- `ping` → primarily Layer 3
- `ss` / `netstat` → Layers 4–5
- `curl` → Layers 4–7
- `tcpdump` / Wireshark → Layers 2–7 (observation)

---

## References

This overview is based on widely accepted open references, including:

- ISO/IEC 7498-1 — OSI Reference Model  
- https://en.wikipedia.org/wiki/OSI_model  
- https://www.cloudflare.com/learning/network-layer/what-is-the-osi-model/  
- https://www.geeksforgeeks.org/open-systems-interconnection-model-osi/

