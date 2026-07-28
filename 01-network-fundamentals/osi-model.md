# OSI Model Overview (Troubleshooting-Oriented)

The **OSI (Open Systems Interconnection) model** is a conceptual framework that describes how data moves between systems across a network.

Although modern networks are typically described using the TCP/IP model, the OSI model remains a valuable tool for troubleshooting because it provides a structured way to analyze where communication failures occur.

Throughout this repository, the OSI model is used to:

- Structure the troubleshooting process
- Narrow down the likely source of a failure
- Select appropriate diagnostic tools
- Apply a logical, layered approach instead of relying on trial and error

---

## Why the OSI Model Is Useful for Troubleshooting

Network problems often appear as application failures—for example, a website that will not load or an API that does not respond. However, the underlying cause may exist at a lower layer, such as DNS resolution, IP routing, firewall rules, or physical connectivity.

The OSI model provides a systematic framework for asking questions such as:

Is there basic network connectivity?
Is name resolution working correctly?
Is the required port reachable?
Is the application responding as expected once connectivity is established?

Rather than treating the OSI model as a list of protocols to memorize, this repository uses it as a practical troubleshooting framework for isolating and diagnosing network issues.

---

## OSI Layers (High-Level Summary)

| Layer | Name | Practical Focus | Typical Devices / Components |
|-----|------|-----------------|-----------------|
| 7 | Application | User-facing services, APIs, DNS, HTTP | Web servers, reverse proxies, application gateways |
| 6 | Presentation | Encryption, encoding, TLS | TLS libraries, SSL termination devices |
| 5 | Session | Session establishment and management | Application servers, session managers |
| 4 | Transport | Ports, TCP/UDP connectivity | Stateful firewalls, load balancers |
| 3 | Network | IP addressing and routing | Routers, Layer 3 switches |
| 2 | Data Link | Local network delivery (Ethernet) | Switches, wireless access points, NICs |
| 1 | Physical | Physical interfaces and signals | Cables, fiber, transceivers, hubs |

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

## OSI Layers Walkthrough

Let's look at an example of a user accessing their Gmail, and what troubleshooting could be done.

### Layer 7 – Application

The user opens Google Chrome and enters:
`https://mail.google.com`

Chrome creates an HTTPS request for the Gmail service.

Possible troubleshooting questions:

- Is Chrome working?
- Does another browser work?
- Is the URL correct?

### Layer 6 – Presentation

The browser negotiates encryption using TLS.
Certificates are exchanged and validated before encrypted communication begins.

Possible troubleshooting questions:

- Is the certificate trusted?
- Is the system clock correct?
- Is TLS negotiation failing?

### Layer 5 – Session

A secure communication session is established between the browser and Google's servers.

Possible troubleshooting questions:

- Does the connection remain established?
- Are repeated reconnects occurring?

### Layer 4 – Transport

TCP establishes a connection using the three-way handshake.
```
SYN
SYN-ACK
ACK
```
HTTPS uses TCP port 443.

Possible troubleshooting questions:

Is port 443 reachable?
Is a firewall blocking the connection?
Are packets being retransmitted?

### Layer 3 – Network

DNS resolves the hostname to an IP address.

Packets are routed through the user's gateway, ISP, and the Internet toward Google's network.

Possible troubleshooting questions:

- Does DNS resolve?
- Is the default gateway reachable?
- Is routing correct?

### Layer 2 – Data Link

Frames are delivered across the local network using MAC addresses.

The client first discovers the MAC address of the default gateway.

Possible troubleshooting questions:

- Is ARP resolving correctly?
- Is the switch forwarding frames?
- Is the correct VLAN configured?

### Layer 1 – Physical

Electrical signals, fiber optics, or Wi-Fi radio transmit the bits.

Possible troubleshooting questions:

- Is the cable connected?
- Is Wi-Fi associated?
- Is the interface up?

Although users experience the problem as "Gmail won't load," the underlying cause could originate at any layer. A structured troubleshooting approach helps isolate the failure instead of relying on trial and error.

| Layer | Typical Tools | 
|-----|------|
| 7	| curl, wget, browser developer tools |
| 6	| openssl, browser certificate viewer |
| 5	| Wireshark |
| 4	| ss, netstat, Test-NetConnection |
| 3	| ping, traceroute, ip, Resolve-DnsName, dig | 
| 2	| ip neigh, arp, Wireshark |
| 1	| ethtool, ip link, NIC status | 


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
