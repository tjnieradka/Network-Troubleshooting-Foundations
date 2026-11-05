# Reading Packets with Wireshark

## 1. Overview
This document demonstrates how Wireshark can be used to capture and examine common network protocols in a lab environment. The examples focus on identifying normal ICMP, DNS, DHCP, TCP, and ARP traffic and examining the packet fields useful for basic network troubleshooting.


## 2. Lab Environment

### 2.1 Systems Used

System |IP Address| Role
-------|----------|--------
Windows 11 client	| 192.168.10.100 |	Wireshark capture and test client
Windows Server 2022 |	192.168.10.10 |	AD domain controller, DNS and DHCP server
Windows Server 2022 |	192.168.10.11 |	Entra ID synchronization server
Ubuntu Server	| 192.168.20.10	| Web server in DMZ

The systems run as virtual machines in a VMware-based lab. VMware DHCP remains enabled on the virtual network, although the Windows Server at 192.168.10.10 provides DHCP for the lab configuration demonstrated here.

### 2.2 Capture Method

Specific Windows commands, such as ping, nslookup, and arp, were used to generate network traffic for each test.

For each capture:
1. Packet capture was started on the Windows 11 client's Ethernet0 interface.
2. The appropriate command or network activity was run to generate traffic.
3. The capture was stopped after the required traffic was recorded.
4. A Wireshark display filter was applied to isolate the relevant protocol.
5. The resulting packets and protocol details were examined.

Display filters were applied after capture rather than capture filters so that the complete packet exchange remained available for analysis.

## 3. ICMP — Echo Request and Reply

### 3.1 Generate ICMP Traffic

To generate ICMP traffic, we are using this command  `ping /n 192.168.10.10` . We are pinging the lab Domain Controller five times from the Wireshark client.

![](../images/wireshark/ping.png)  

### 3.2 Apply the ICMP Display Filter

As shown in the screenshot near the top left-hand corner, we applied the `icmp` filter.

![](../images/wireshark/ping-in-wireshark.png)  

### 3.3 Analyze the Packets

The Wireshark screenshot shows the following: 

- 192.168.10.100 (Source) sends an Echo Request to 192.168.10.10 (Destination).  
- 192.168.10.10 returns an Echo Reply.  
- Wireshark associates each request with its corresponding reply in the Info column. 
- Request/reply pairs demonstrate successful IP connectivity.  

Selecting an individual packet allows additional information to be examined in the Packet Details pane, including the IPv4 source and destination addresses and ICMP protocol information.

## 4. DNS — Name Resolution

### 4.1 Generate a DNS Query

To generate DNS traffic, we are using this command  `nslookup vanec1-w2022`. We are trying to resolve the IP address of the Entra ID synchronization server from the Wireshark client.

![](../images/wireshark/nslookup.png)  

### 4.2 Apply the DNS Display Filter

As shown in the screenshot near the top left-hand corner, we applied the `dns` filter.

![](../images/wireshark/nslookup-in-wireshark.png)  

### 4.3 Analyze the Query and Response

The `dns` display filter isolates DNS traffic in the capture.

Packets 18 and 19 show a successful DNS lookup between the Windows 11 client (192.168.10.100) and the DNS server (192.168.10.10).  
- Packet 18: The client sends an A record query for vanec1-w2022.tntechdemo01.com.  
- Packet 19: The DNS server responds with the IPv4 address 192.168.10.11.  
- The exchange demonstrates successful hostname-to-IPv4 address resolution using the lab DNS server.  
- The packet details also show that the DNS query is being sent using UDP destination port 53.  
- Additional DNS traffic may appear in the capture because the client can perform other DNS queries during the same period, including reverse lookups and IPv6 (AAAA) queries.  

## 5. DHCP — Address Configuration

### 5.1 Generate DHCP Traffic

![](../images/wireshark/dhcp.png)  

### 5.2 Apply the DHCP Display Filter

![](../images/wireshark/dhcp-discover.png)  

![](../images/wireshark/dhcp-offer.png)  

![](../images/wireshark/dhcp-request.png)  

![](../images/wireshark/dhcp-acknowledge.png)  

### 5.3 Analyze the DHCP Exchange

## 6. TCP — Connection Establishment

### 6.1 Generate TCP Traffic
![](../images/wireshark/tcp.png)  

### 6.2 Apply the TCP Display Filter

![](../images/wireshark/tcp-get-2.png)  

![](../images/wireshark/tcp-http-2.png)  

### 6.3 Analyze the TCP Three-Way Handshake

## 7. ARP — Address Resolution

### 7.1 Generate ARP Traffic

![](../images/wireshark/arp.png) 

### 7.2 Apply the ARP Display Filter

![](../images/wireshark/arp-broadcast-in-wireshark.png) 

![](../images/wireshark/arp-reply-in-wireshark.png) 

### 7.3 Analyze the ARP Request and Reply

## 8. Summary
