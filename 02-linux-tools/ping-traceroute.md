## Overview

`ping` verifies basic IP connectivity using ICMP Echo Requests in both Linux and Windows, while traceroute (Linux) and tracert (Windows) identify the path packets take through a network.

## Usage
- Verify host connectivity
- Check latency
- Determine where communication stops
- Verify default gateway
- Basic reachability testing

## Common Syntax 

### Linux
`ping google.com`  
`ping -c 4 google.com`  
`traceroute google.com`  

### Windows
`ping google.com`  
`tracert google.com`  
`pathping google.com`  

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
