# TCP/IP Basics
## Purpose

The TCP/IP protocol suite forms the foundation of modern computer networking and underpins communication across local networks and the Internet. 
While the OSI model provides a conceptual framework for troubleshooting, TCP/IP describes the protocols used in real-world networks.

Understanding IP addressing, subnetting, and routing is essential when diagnosing connectivity issues, as many network problems originate from 
incorrect addressing or routing rather than application failures.

## IPv4 Addressing
The following example illustrates an IPv4 address and its associated subnet.

`192.168.1.25`

An IPv4 address consists of 32 bits divided into four 8-bit octets. Together with the subnet mask, the address identifies both the network and the individual host.

```text
192.168.1.25/24
Subnet Mask:  255.255.255.0

Network: 192.168.1.0
Host ID:    25
```
## Subnet Masks
A subnet mask defines which portion of an IP address identifies the network and which portion identifies the individual host. Devices use the subnet mask to determine whether the destination IP address resides on the local subnet or on a remote network.

In previous example, the first three octets identify the network (192.168.1.0), while the final octet identifies the individual host (25). Because this is a /24 network, devices with addresses beginning 192.168.1.x are considered part of the same local subnet.

If the subnet mask is incorrect, a device may incorrectly determine whether a destination is local or remote, resulting in failed communication or traffic being sent to the wrong destination.

## Default Gateway

```text
PC
192.168.1.25
      │
      │
Ethernet Switch
      │
      │
Router (Default Gateway)
192.168.1.1
      │
      │
Internet

```

In this example, the router (192.168.1.1) serves as the default gateway for the local network.

When the destination IP address is within the same subnet, devices communicate directly with one another. If the destination is located on a different network, the client forwards the traffic to the default gateway, which routes the packets toward their destination.

If the default gateway is unreachable or incorrectly configured, communication outside the local subnet will fail, although communication with devices on the same subnet may still succeed.

## Private IPv4 Address Ranges

Private IPv4 address ranges are reserved for use within internal networks and are not routable on the public Internet. Organizations and home networks commonly use these ranges to assign addresses to local devices. When Internet access is required, Network Address Translation (NAT) translates one or more private IP addresses into a public IP address, allowing internal devices to communicate with external networks.

```text
Private Range	Typical Use
10.0.0.0/8	Large enterprise networks
172.16.0.0/12	Medium-sized enterprise networks
192.168.0.0/16	Home and small office networks
```
During network troubleshooting, it is useful to recognize private IP addresses, as they indicate that NAT or another routing device is typically required for communication with the public Internet.

## IP Address Classes
Historically, IPv4 networks were divided into Class A, B, and C networks. Current networking instead uses Classless Inter-Domain Routing (CIDR), which allows more flexible allocation of address space. 

Class | First Octet | Default Mask
------|-------------|-------------
A |	1–126	| /8
B |	128–191 |	/16
C |	192–223 |	/24


## IPv6
IPv6 uses 128-bit addresses and is becoming increasingly common in enterprise and cloud environments. Although this repository focuses primarily on IPv4 troubleshooting examples, the same diagnostic principles apply to IPv6.

Example:

```text
IPv6 Address: 2001:db8:100:1::25/64

Network Prefix: 2001:db8:100:1::/64
Host ID:        ::25
```
## Troubleshooting

| Question | Example Tool |
|----------|--------------|
| What's my IP? |	`ip addr`, `ipconfig`
| What's my gateway? |	`ip route`, `route print`. `ipconfig /all`
| Can I reach the default gateway? | `ping`
| Is routing correct? |	`traceroute`, `tracert`
| Is DNS the problem? | `dig`, `Resolve-DnsName`, `nslookup`

```text

Network Flow

Application
      │
      ▼
Needs remote server?
      │
      ▼
Destination on local subnet?
      │
 ┌────┴─────┐
 │          │
Yes        No
 │          │
Direct     Forward to
delivery   Default Gateway
```
The subnet mask determines whether the destination is on the local subnet. If it is not, the packet is forwarded to the configured default gateway for routing to another network.
