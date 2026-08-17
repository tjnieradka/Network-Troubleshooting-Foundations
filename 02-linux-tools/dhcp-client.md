# DHCP Client Configuration

## Overview

Dynamic Host Configuration Protocol (DHCP) automatically provides network configuration to clients.

A DHCP client can receive configuration such as:

* IP address
* Subnet mask or prefix length
* Default gateway
* DNS server
* Lease information

On Rocky Linux, NetworkManager manages network connections and DHCP configuration. The `nmcli` command-line utility can be used to inspect and manage these connections.

## Key Concepts

### DHCP

DHCP automatically provides network configuration to clients instead of requiring administrators to manually configure each system.

A DHCP client typically receives an IP address and other network settings from a DHCP server.

### DHCP Lease

An address assigned through DHCP is normally provided for a limited period called a **lease**.

The client can renew the lease to continue using the configuration.

Linux tools may display the remaining valid and preferred lifetime of a dynamically assigned address.

### Dynamic vs. Static Addressing

A **dynamic IP address** is assigned automatically through DHCP.

A **static IP address** is manually configured and normally remains unchanged unless an administrator modifies the configuration.

The `ip addr` command can indicate when an address is dynamically assigned.

For example:

`inet 192.168.35.141/24 ... dynamic ...`

The `dynamic` attribute indicates that the IPv4 address was assigned dynamically rather than configured as a permanent static address.

### NetworkManager

NetworkManager is a Linux service that manages network interfaces and connection profiles.

Rocky Linux uses NetworkManager, and its command-line interface is:

`nmcli`

`nmcli` can display interface status, connection profiles, IP addresses, routes, gateways, DNS configuration, and other network settings.

### Device vs. Connection

NetworkManager distinguishes between a **device** and a **connection profile**.

A device is a network interface such as:

`ens160`

A connection profile contains the configuration that NetworkManager applies to that device.

The distinction is useful when troubleshooting because an interface can exist even when its expected connection profile is not active.

### Default Gateway

The default gateway is the router used to reach destinations outside the local subnet.

A DHCP server can provide the default gateway to the client as part of its network configuration.

### DNS Configuration

DHCP can also provide the address of a DNS resolver.

DNS allows applications to resolve hostnames such as:

`www.google.com`

to IP addresses.

A system can therefore have valid IP connectivity while still experiencing name-resolution problems if its DNS configuration is incorrect.


## Usage

Use Linux network and NetworkManager commands to:

* Verify that an interface received an IP address dynamically
* Identify the IP address and subnet assigned to an interface
* Verify the default gateway
* Identify the configured DNS server
* Check the state of network interfaces and connections
* Disconnect and reconnect an interface
* Request new network configuration from DHCP
* Troubleshoot a client that cannot obtain or use a DHCP configuration

When troubleshooting a client with no network connectivity, verifying its IP configuration can help determine whether the problem begins with DHCP or elsewhere in the network.

## Common Commands

1. **Display Interface Addresses**  
`ip addr`

Displays network interfaces and their assigned IPv4 and IPv6 addresses.

A dynamically assigned IPv4 address may include the `dynamic` attribute.

2. **Display NetworkManager Connections**  
`nmcli connection show`

Displays NetworkManager connection profiles and the devices associated with them.

3. **Display Detailed Device Configuration**  
`nmcli device show`

Displays detailed network configuration including:

* Interface state
* IPv4 address
* Default gateway
* Routes
* DNS server
* IPv6 configuration

4. **Display a Specific Device**

`nmcli device show ens160`

Displays detailed information for the `ens160` interface.

5. **Display Device Status**
`nmcli device status`

Provides a concise view of NetworkManager devices and their current state.

6. **Disconnect an Interface**
`sudo nmcli device disconnect ens160`


Disconnects the interface and deactivates its current NetworkManager connection.

> Running this command on a remote system can terminate the administrator's network connection.

7. **Reconnect an Interface**
`sudo nmcli device connect ens160`

Reconnects the interface.

If the connection profile uses automatic IPv4 configuration, NetworkManager obtains DHCP configuration when the connection is activated.

8. **Verify the Configuration**
`ip addr`

or:

`nmcli device show ens160`

can be used after reconnecting the interface to verify that network configuration has been restored.

## Practical Examples

### Verify a Dynamically Assigned Address

```bash
ip addr
```

Example output may contain:

```text
2: ens160: <BROADCAST,MULTICAST,UP,LOWER_UP>
    inet 192.168.35.141/24 ... scope global dynamic ... ens160
```

The output confirms that:

* `ens160` is active
* `192.168.35.141` is the assigned IPv4 address
* `/24` is the network prefix
* `dynamic` indicates that the address was assigned dynamically

This is a quick way to verify that the interface has obtained an IPv4 configuration.

### Identify the Active NetworkManager Connection

```bash
nmcli connection show
```

The output identifies available NetworkManager connection profiles and the devices using them.

A connection associated with `ens160` confirms that NetworkManager has a connection profile for the Ethernet interface.

This can help distinguish between a problem with the physical or virtual interface and a problem with its NetworkManager configuration.

### Verify Address, Gateway, and DNS Configuration

```bash
nmcli device show
```

For `ens160`, important fields include:

```text
IP4.ADDRESS[1]:    192.168.35.141/24
IP4.GATEWAY:       192.168.35.2
IP4.DNS[1]:        192.168.35.2
```

These values confirm that the client has:

* An IPv4 address and subnet prefix
* A default gateway
* A DNS server

This provides a more complete view of the client's network configuration than checking the IP address alone.

### Reconnect the Interface and Refresh DHCP Configuration

Disconnect the interface:

```bash
sudo nmcli device disconnect ens160
```

Reconnect it:

```bash
sudo nmcli device connect ens160
```

Then verify the resulting configuration:

```bash
ip addr
```

If the connection profile uses DHCP, reconnecting the interface causes NetworkManager to activate the connection and obtain network configuration.

In this example, `ens160` receives a dynamic IPv4 address again after the connection is reactivated.

> **Caution:** Disconnecting an interface interrupts network connectivity. This should not be performed casually on a production system or through the same remote connection that depends on the interface.

### DHCP Troubleshooting Workflow

If a Linux client cannot communicate with the network, begin by checking its address:

```bash
ip addr
```

Then inspect its NetworkManager configuration:

```bash
nmcli device show ens160
```

Verify:

1. The interface is connected.
2. An appropriate IPv4 address is assigned.
3. The subnet prefix is correct.
4. A default gateway is configured.
5. A DNS server is configured.

If the configuration appears correct, continue troubleshooting with tools such as `ping`, `dig`, `ss`, or `tcpdump` depending on the symptoms.

---

### Note About dhclient

Some Linux environments may include the traditional `dhclient` utility for manually requesting or renewing DHCP leases.

For example:

```bash
sudo dhclient
```

However, DHCP client management varies between Linux distributions and network-management frameworks.

On modern Rocky Linux systems using NetworkManager, `nmcli` should generally be used to manage NetworkManager-controlled connections rather than relying on `dhclient` as the primary DHCP management tool.
