## Overview

`ping`, `traceroute`, and `mtr` are Linux network diagnostic tools used to test connectivity and investigate the network path between a local system and a destination.

- `ping` tests basic IP reachability and measures round-trip response time.
- `traceroute` identifies the sequence of network hops toward a destination.
- `mtr` combines features of ping and traceroute to continuously measure latency and packet loss across the network path.

Together, these tools can help determine whether a connectivity problem is local, occurs somewhere along the network path, or involves the destination.

## Key Concepts

- **ICMP**
  Internet Control Message Protocol (ICMP) is used for network diagnostics and error reporting.  
  `ping` normally sends ICMP Echo Request packets and waits for ICMP Echo Reply packets from the destination.  
  A successful response confirms that IP connectivity exists between the systems and that ICMP traffic is permitted.  

- **Round-Trip Time**
  Round-trip time (RTT) measures how long it takes for a packet to travel to a destination and for the response to return.  
  `ping` reports RTT in milliseconds.  
  Higher response times indicate greater latency, although normal latency varies depending on distance, network conditions, and the destination.  

- **Packet Loss**
  Packet loss occurs when transmitted packets do not receive responses.
  For example: `4 packets transmitted, 4 received, 0% packet loss` indicates that all four ICMP Echo Requests received responses.  
  Packet loss can indicate network congestion, connectivity problems, filtering, or other network conditions. However, packet loss shown for an intermediate router does not automatically mean that the router is dropping forwarded traffic.  

- **Network Hops**
  A hop represents a router or Layer 3 device that a packet passes through while travelling toward its destination.  
  `traceroute` and `mtr` display these intermediate hops to help identify the path traffic takes across a network.
  
- **TTL**
  Time To Live (TTL) is an IP header value that limits how many routers a packet can pass through.  
  Each router decreases the TTL value by one. When TTL reaches zero, the router discards the packet and normally returns an ICMP Time Exceeded message.  
  `traceroute` uses this behaviour to discover routers along the path by sending packets with progressively increasing TTL values.

- **ICMP Filtering**
   Not every router or destination responds to ICMP diagnostic traffic.
   A missing response from an intermediate hop does not necessarily indicate a network failure if later hops and the final destination continue responding.
   This is important when interpreting traceroute and `mtr` results.

## Usage

Use these commands to:

- Verify whether a local or remote host is reachable
- Test connectivity to the default gateway
- Measure round-trip latency
- Identify packet loss
- Determine the network path toward a destination
- Identify where communication appears to stop along a route
- Compare latency across different network hops
- Help distinguish local network problems from upstream network problems
- Investigate possible routing or firewall issues

These tools primarily test network-layer connectivity. A successful `ping`, for example, confirms that ICMP communication is working but does not prove that an application or service such as HTTPS, SSH, or DNS is functioning.

Similarly, a failed ICMP test does not necessarily mean that the destination is offline because routers, firewalls, and hosts may block or deprioritize ICMP traffic.


## Common Commands

1. **Test Connectivity with `ping`** - Continuously sends ICMP Echo Requests until the command is stopped with Ctrl+C.
`ping google.com`

2. **Send a Limited Number of Ping Requests** - Sends four ICMP Echo Requests and then displays summary statistics.
`ping -c 4 google.com`

3. **Test the Default Gateway** - Tests connectivity between the Linux system and its local default gateway.
`ping -c 4 192.168.35.2`

If the gateway cannot be reached, troubleshooting should generally begin with the local network configuration before investigating Internet connectivity.

4. **Trace the Network Path** - Displays the sequence of network hops toward the destination. Typical Linux `traceroute` commonly uses UDP probes by default.
`traceroute google.com`

5. **Trace Using ICMP** - Uses ICMP Echo packets instead of the default UDP probes. This can produce more useful results on networks where the default traceroute probes are filtered.
`sudo traceroute -I google.com`

6. **Monitor a Network Path with `mtr`** - Continuously displays network hops along with latency and packet-loss statistics.
`mtr google.com`

8. **Generate an mtr Report** - Runs ten measurement cycles and then produces a report. The report format is useful for documentation and troubleshooting because it provides a fixed set of results rather than continuously updating the terminal.
`mtr -r -c 10 google.com`


## Practical Examples

## Typical Troubleshooting Scenarios
- Cannot reach gateway
- Internet unavailable
- High latency
- Routing issue
- Firewall blocking ICMP

## Common Mistakes
- Assuming ping proves the application is working
- Assuming no ping means the server is offline
- Ignoring packet loss

## Related Commands
`Test-NetConnection` (Windows PowerShell)  
`tracepath` (Linux)  
`mtr` (Linux)  
