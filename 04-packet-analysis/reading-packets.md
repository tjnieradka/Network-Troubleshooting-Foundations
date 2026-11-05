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
### 3.2 Apply the ICMP Display Filter
### 3.3 Analyze the Packets

## 4. DNS — Name Resolution

### 4.1 Generate a DNS Query
### 4.2 Apply the DNS Display Filter
### 4.3 Analyze the Query and Response

## 5. DHCP — Address Configuration

### 5.1 Generate DHCP Traffic
### 5.2 Apply the DHCP Display Filter
### 5.3 Analyze the DHCP Exchange

## 6. TCP — Connection Establishment

### 6.1 Generate TCP Traffic
### 6.2 Apply the TCP Display Filter
### 6.3 Analyze the TCP Three-Way Handshake

## 7. ARP — Address Resolution

### 7.1 Generate ARP Traffic
### 7.2 Apply the ARP Display Filter
### 7.3 Analyze the ARP Request and Reply

## 8. Summary
