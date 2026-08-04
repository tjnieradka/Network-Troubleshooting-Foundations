# Overview

A network port identifies a specific service or application running on a host. While an IP address identifies the destination device, the port identifies the service on that device, allowing multiple network services to operate simultaneously.
For example, a web server may use TCP port 443 for HTTPS, while an SSH server listens on TCP port 22.

## Port Numbers in URLs
For example, when the following URL is entered into the browser, it actually defaults to default http port 80

```http://example.com``` --> ```http://example.com:80```

Likewise, the following defaults to default https port 443

```https://example.com``` --> ```https://example.com:443```

When a service uses a non-default port, the port number must be specified explicitly.  In this example the port is 8443.

```https://example.com:8443```

## Common Ports

| Port | Protocol | Service | Typical Use |
|-----:|:--------:|---------|-------------|
| 20/21 | TCP | FTP | Legacy protocol for file transfers. Port 21 is the control channel; port 20 is traditionally used for data transfer in active mode. |
| 22 | TCP | SSH | Secure remote administration of Linux, Unix, and network devices; also supports secure file transfer (SCP/SFTP). |
| 25 | TCP | SMTP | Used for sending email between mail servers; often restricted by ISPs for end-user devices. |
| 53 | TCP/UDP | DNS | Resolves hostnames to IP addresses. UDP is used for most queries; TCP is used for zone transfers and larger responses. |
| 67/68 | UDP | DHCP | Automatically assigns IP configuration to clients. Port 67 is the DHCP server; port 68 is the DHCP client. |
| 80 | TCP | HTTP | Unencrypted web traffic. Commonly redirects users to HTTPS. |
| 110 | TCP | POP3 | Retrieves email by downloading messages from a mail server. |
| 123 | UDP | NTP | Synchronizes system clocks with time servers. Accurate time is important for authentication and logging. |
| 143 | TCP | IMAP | Retrieves and manages email while keeping messages on the mail server. |
| 161 | UDP | SNMP | Used to monitor and manage network devices such as switches, routers, and servers. |
| 389 | TCP/UDP | LDAP | Directory service communication, including Microsoft Active Directory and other LDAP directories. |
| 443 | TCP | HTTPS | Secure web traffic encrypted using TLS. One of the most commonly used Internet ports. |
| 636 | TCP | LDAPS | LDAP communication secured with TLS encryption. |
| 3389 | TCP | Remote Desktop (RDP) | Remote graphical access to Windows systems. |
| 445 |	TCP	| SMB	| Windows file sharing, shared folders, and Active Directory communication. |
| 1433 |	TCP	| Microsoft SQL Server |	Default port for Microsoft SQL Server client connections. |
| 3306 |	TCP	| MySQL | Default port for MySQL database servers. |
| 5432 |	TCP	| PostgreSQL |	Default port for PostgreSQL database servers. |
