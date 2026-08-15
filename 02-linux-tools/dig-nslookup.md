## Overview

`dig` and `nslookup` are command-line tools used to query the Domain Name System (DNS) and troubleshoot name resolution.

`dig` provides detailed DNS information and is commonly used on Linux for DNS troubleshooting and analysis.

`nslookup` provides simpler DNS query output and is useful for quickly checking whether a hostname or IP address can be resolved.



## Key Concepts
- **Forward DNS Lookup** - A forward lookup resolves a hostname to an IP address.  
For example, www.example.com → 93.184.216.34
DNS `A` records map hostnames to IPv4 addresses, while `AAAA` records map hostnames to IPv6 addresses.  

- **Reverse DNS Lookup** - A reverse lookup attempts to resolve an IP address back to a hostname using a DNS PTR record.  
IP address → hostname  
Not every IP address has a corresponding PTR record, so a failed reverse lookup does not necessarily indicate a network problem.  

- **DNS Record Types** - Common DNS record types include:

  Record |	Purpose
  -------|---------
  `A`	| Maps a hostname to an IPv4 address
  `AAAA` |	Maps a hostname to an IPv6 address
  `CNAME`	| Creates an alias for another hostname
  `MX`	| Identifies mail servers for a domain
  `NS`	| Identifies authoritative DNS servers
  `PTR`	| Maps an IP address back to a hostname
  `TXT`	| Stores text information associated with a domain

- **DNS  Server** - DNS queries are sent to a DNS resolver configured on the system.  
`dig` displays the DNS server that answered the query in the SERVER field.  
A specific DNS server can also be queried directly, which is useful for comparing DNS results.  

- **DNS Response Codes** - DNS responses include status codes that help identify whether a query succeeded.
  Common examples include:

    `NOERROR` — the DNS query completed successfully
    `NXDOMAIN` — the requested domain name does not exist
    `SERVFAIL` — the DNS server could not successfully process the query
    `REFUSED` — the DNS server refused to perform the requested query

## Usage

Use `dig` and `nslookup` to:

- Verify that a hostname resolves to an IP address
- Check which DNS server is responding to a query
- Query specific DNS record types
- Troubleshoot name resolution failures
- Perform reverse DNS lookups
- Compare results from different DNS servers
- Identify DNS errors such as NXDOMAIN

## Common Commands

1. **Basic Lookup with `dig`** - Queries DNS information for google.com.  
`dig google.com`
The output includes the DNS response, returned records, query time, and DNS server used.  

2. **Display Only the Answer** - Displays a simplified result without the full DNS query information.  
`dig google.com +short` 

3. **Query an A Record** - Queries the IPv4 address records associated with the domain.  
`dig google.com A`

4. **Query an MX Record** - Displays the mail servers responsible for receiving email for the domain.  
`dig google.com MX`
 
5. **Query Name Servers** - Displays the authoritative DNS servers associated with the domain.  
`dig google.com NS`

6. **Query a Specific DNS Server** - Sends the DNS query directly to the specified DNS server instead of using the system's configured resolver.  
`dig @8.8.8.8 google.com`  

   This can help determine whether a DNS problem is related to the local DNS server.  

7. **Reverse Lookup** - Performs a reverse DNS lookup by querying for a PTR record associated with the IP address.  
`dig -x 8.8.8.8`

8. **Basic Lookup with `nslookup`** - Displays the DNS server used for the query and the IP address or addresses returned for the hostname.  
`nslookup google.com`

9. **Reverse Lookup with `nslookup`** - Attempts to resolve the IP address to a hostname using a PTR record.  
`nslookup 8.8.8.8`

## Practical Examples

View DNS resolution using `dig`.  

![Viewing DNS resolution using `dig`](../images/linux/dig-google.png)  

View DNS resolution using `dig` and a specific DNS server.  

![Viewing DNS resolution using `dig`and a specific DNS server](../images/linux/dig-at.png)  

View DNS resolution using `dig` where output shows a MX record.

![Viewing DNS resolution using `dig` where output shows MX](../images/linux/dig-google.com-mx.png) 

View DNS resolution using `dig` where output shows no MX record (`ANSWER: 0`)

![Viewing DNS resolution using `dig` where output shows no MX](../images/linux/dig-no-MX.png) 

View DNS resolution using `nslookup`

![Viewing DNS resolution using `nslookup`](../images/linux/nslookup.png) 

View reverse DNS resolution using `nslookup`

![Viewing reverse DNS resolution using `nslookup`](../images/linux/nslookup-reverse.png) 

