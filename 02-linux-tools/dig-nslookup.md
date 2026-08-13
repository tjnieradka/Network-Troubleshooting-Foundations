## Overview
Test DNS resolution or configuration.

## Usage 
- Name resolution failures
- Verify DNS server
- Check DNS records

## Common Syntax

### Linux

`dig google.com`  
`dig @8.8.8.8 google.com`  
`nslookup google.com`  

### Windows
`Resolve-DnsName google.com`  
`nslookup google.com`  

## Practical Examples

Show

A record
MX record
Reverse lookup

## Troubleshooting
- Wrong DNS server
- NXDOMAIN
- Timeout
- Cached response

Related Commands
`ipconfig /flushdns` (Windows)
`systemd-resolve` (Linux)
