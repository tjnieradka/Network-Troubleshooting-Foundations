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

```
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

```
PC
192.168.1.25
      │
      │
Switch
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

