## Overview

Explain what DHCP does in one paragraph.

## Usage 
- No IP address assigned
- APIPA address on Windows equivalent (or no lease on Linux)
- Wrong IP configuration
- Cannot reach the network after moving to another VLAN
- Renewing an expired lease

## Common Commands

Rocky Linux (NetworkManager)

`nmcli device show`  
`nmcli connection show`  
`ip addr`  

If dhclient is installed:

`sudo dhclient`  

Release and renew:

`sudo dhclient -r`  
`sudo dhclient`  

Some modern distributions use NetworkManager or systemd-networkd instead of invoking dhclient directly.

## Troubleshooting
- No lease received
- Incorrect subnet
- Incorrect gateway
- DHCP server unavailable
