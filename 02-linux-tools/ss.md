## Overview

`ss` (socket statistics) is a Linux command used to display information about network sockets, listening ports, and active network connections.

It can be used to determine which TCP or UDP ports are listening, identify established connections, examine TCP connection states, and associate network sockets with processes.

`ss` is commonly used nowadays as a replacement for the older `netstat` command on Linux.

## Key Concepts

- **Network Sockets**  
  A socket represents an endpoint used by a process for network communication.  
  A socket is associated with information such as:

    - Protocol
    - Local IP address
    - Local port
    - Remote IP address
    - Remote port
  - Connection state

  `ss` displays these sockets and their current state.

- **Listening Ports**
  A listening socket indicates that a process is waiting for incoming connections on a particular TCP port.
  For example:
  `0.0.0.0:22` indicates that a service is listening on TCP port 22 on all IPv4 interfaces.

  A listening service does not necessarily mean that the port is reachable from another system. A firewall or other network control may still block remote access.

- **TCP and UDP**
  TCP is connection-oriented and maintains connection states such as LISTEN, ESTAB, and TIME-WAIT.  
  UDP is connectionless and does not establish connections in the same way as TCP. UDP sockets therefore do not use the same connection states.  

- **Local and Peer Addresses**
  `ss` displays both local and peer endpoints.  
  Local Address — the local IP address and port used by the system  
  Peer Address — the remote endpoint associated with the connection
    
  For a listening socket, there may not yet be a specific remote peer.  

- **Binding**
  A service can listen on a specific interface or on multiple interfaces.
  Examples:
  `127.0.0.1:8080`
  The service is listening only on the local loopback interface and normally cannot be reached directly from another system.

  `0.0.0.0:8080`
  The service is listening on port 8080 on all IPv4 interfaces.

  `[::]:8080`
  The service is listening using an IPv6 wildcard address. Exact IPv4 behavior can depend on the system's IPv6 socket configuration.

  Understanding the bind address is important when troubleshooting a service that works locally but cannot be reached remotely.

- **TCP Connection States**

  Common TCP states include:

  State	| Meaning
  ------|--------
  `LISTEN` |	Waiting for incoming connections
  `ESTAB`	| An active TCP connection has been established
  `TIME-WAIT` | A closed connection is temporarily retained to handle delayed packets
  `SYN-SENT` |	A connection request was sent and is waiting for a response
  `SYN-RECV` |	A connection request was received and is being processed
  `CLOSE-WAIT` | The remote side closed the connection and the local application has not yet fully closed it

  TCP states can provide useful information about where a connection may be failing.


## Usage

Use `ss` to:
- Verify that a service is listening on the expected port
- Identify listening TCP and UDP ports
- View established network connections
- Examine TCP connection states
- Identify which process is using a network port
- Determine whether a service is bound to the expected IP address
- Investigate unexpected listening services
- Help identify port conflicts or connection problems

For example, if an application cannot be reached remotely, `ss` can first determine whether the application is actually listening on the expected port.

If the service is listening correctly, troubleshooting can then continue with firewall rules, routing, or remote connectivity testing.

## Common Commands

1. **Display Listening TCP and UDP Ports**  
  `ss -tuln`  

  Options:  

  `-t` — TCP sockets  
  `-u` — UDP sockets  
  `-l` — listening sockets  
  `-n` — display numeric addresses and ports instead of resolving names  

  This provides a quick view of network services listening on the system.  

2. **Display TCP Connections**  
  `ss -tan`  

  Displays TCP sockets using numeric addresses and ports.  

  This includes both listening sockets and active or recently closed TCP connections.  

3. **Display Listening Ports and Processes**  
  `sudo ss -tulpn`

  Adds process information to the listening TCP and UDP sockets.  

  The `-p` option displays the process associated with each socket. Root privileges may be required to display complete process information.  

4. **Display Established TCP Connections**  
  `ss -tn state established`  

  Displays currently established TCP connections.  

5. **Display Listening TCP Sockets**  
  `ss -ltn`  

  Displays only listening TCP sockets.  

6. **Check a Specific Port**  
  `ss -ltn | grep ':22'`  

  Checks whether a TCP service is listening on port 22.    

## Practical Examples
Listening port
Established connection
TIME_WAIT


