## Overview
Verify port or services configuration.

## Usage
- Verify listening services
- Verify established connections
- Identify open ports

## Common Syntax

### Linux

`ss -tuln`  
`ss -tan`  
`ss -tulpn`  

### Windows
`Get-NetTCPConnection`  
`netstat -ano`  

## Practical Examples
Listening port
Established connection
TIME_WAIT

## Troubleshooting
- Service not listening
- Wrong port
- Port conflict
- Too many connections

## Related Commands
`lsof` (Linux)  
`Test-NetConnection` (Windows)  
