# Scanning Networks
> Network scanning refers to a set of procedures performed to identify the hosts, ports, and services running in a network.

<br>

Host Discovery using Nmap: `nmap -sn -PR [Target IP Address] `
- > -sn: disables port scan and -PR: performs ARP ping scan.
- > -PU: performs the UDP ping scan.
- > -PE: performs the ICMP ECHO ping scan.
- > -PP: performs the ICMP timestamp ping scan.
- ICMP Address Mask Ping Scan: This technique is an alternative for the traditional ICMP ECHO ping scan, which are used to determine whether the target host is live specifically when administrators block the ICMP ECHO pings.
  - nmap -sn -PM [target IP address]

- TCP SYN Ping Scan: This technique sends empty TCP SYN packets to the target host, ACK response means that the host is active.
  - nmap -sn -PS [target IP address]

- TCP ACK Ping Scan: This technique sends empty TCP ACK packets to the target host; an RST response means that the host is active.

  - nmap -sn -PA [target IP address]
- IP Protocol Ping Scan: This technique sends different probe packets of different IP protocols to the target host, any response from any probe indicates that a host is active.
  - nmap -sn -PO [target IP address]

sx arp [Target subnet] 
- sx arp [Target subnet] --json | tee arp.cache
- cat arp.cache | sx tcp -p 1-65535 [Target IP address] 
- cat arp.cache | sx udp --json -p [Target Port] 10.10.1.11

nmap -sS -v [Target IP Address] 
- -sS: performs the stealth scan/TCP half-open scan and -v: enables the verbose output (include all hosts and ports in the output).
    > The stealth scan involves resetting the TCP connection between the client and server abruptly before completion of three-way handshake signals, and hence leaving the connection half-open. This scanning technique can be used to bypass firewall rules, logging mechanisms, and hide under network traffic.

nmap -sX -v [Target IP Address]
- -sX: performs the Xmas scan
    > Xmas scan sends a TCP frame to a target system with FIN, URG, and PUSH flags set. If the target has opened the port, then you will receive no response from the target system. If the target has closed the port, then you will receive a target system reply with an RST.

- -sM: performs the TCP Maimon scan
    > In the TCP Maimon scan, a FIN/ACK probe is sent to the target; if there is no response, then the port is Open|Filtered, but if the RST packet is sent as a response, then the port is closed.

-  -sA: performs the ACK flag probe scan
    > The ACK flag probe scan sends an ACK probe packet with a random sequence number; no response implies that the port is filtered (stateful firewall is present), and an RST response means that the port is not filtered.

- -sU: performs the UDP scan
    > The UDP scan uses UDP protocol instead of the TCP. There is no three-way handshake for the UDP scan. It sends UDP packets to the target host; no response means that the port is open. If the port is closed, an ICMP port unreachable message is received.

- -sV: detects service versions.
- -A: enables aggressive scan. The aggressive scan option supports OS detection (-O), version scanning (-sV), script scanning (-sC), and traceroute (--traceroute). You should not use -A against target networks without permission.

Banner grabbing, or OS fingerprinting, is a method used to determine the OS that is running on a remote target system.

There are two types of OS discovery or banner grabbing techniques:

- Active Banner Grabbing Specially crafted packets are sent to the remote OS, and the responses are noted, which are then compared with a database to determine the OS. Responses from different OSes vary, because of differences in the TCP/IP stack implementation.

- Passive Banner Grabbing This depends on the differential implementation of the stack and the various ways an OS responds to packets. Passive banner grabbing includes banner grabbing from error messages, sniffing the network traffic, and banner grabbing from page extensions.

Identify the target system’s OS with Time-to-Live (TTL):

![image](https://user-images.githubusercontent.com/79740895/226240083-d6fba9dd-4e9d-4490-8a0a-c9dd2c3e320c.png)

nmap --script smb-os-discovery.nse [Target IP Address]
> --script: specifies the customized script and smb-os-discovery.nse: attempts to determine the OS, computer name, domain, workgroup, and current time over the SMB protocol (ports 445 or 139).

unicornscan [Target IP Address] -Iv
> In this command, -I specifies an immediate mode and v specifies a verbose mode.

## Scan beyond IDS and Firewall

An Intrusion Detection System (IDS) and firewall are the security mechanisms intended to prevent an unauthorized person from accessing a network. However, even IDSs and firewalls have some security limitations. Firewalls and IDSs intend to avoid malicious traffic (packets) from entering into a network, but certain techniques can be used to send intended packets to the target and evade IDSs/firewalls.

Techniques to evade IDS/firewall:

- Packet Fragmentation: Send fragmented probe packets to the intended target, which re-assembles it after receiving all the fragments
- Source Routing: Specifies the routing path for the malformed packet to reach the intended target
- Source Port Manipulation: Manipulate the actual source port with the common source port to evade IDS/firewall
- IP Address Decoy: Generate or manually specify IP addresses of the decoys so that the IDS/firewall cannot determine the actual IP address
- IP Address Spoofing: Change source IP addresses so that the attack appears to be coming in as someone else
- Creating Custom Packets: Send custom packets to scan the intended target beyond the firewalls
- Randomizing Host Order: Scan the number of hosts in the target network in a random order to scan the intended target that is lying beyond the firewall
- Sending Bad Checksums: Send the packets with bad or bogus TCP/UPD checksums to the intended target
- Proxy Servers: Use a chain of proxy servers to hide the actual source of a scan and evade certain IDS/firewall restrictions
- Anonymizers: Use anonymizers that allow them to bypass Internet censors and evade certain IDS and firewall rules

nmap -f [Target IP Address]
- -f switch is used to split the IP packet into tiny fragment packets.
    > Packet fragmentation refers to the splitting of a probe packet into several smaller packets (fragments) while sending it to a network. When these packets reach a host, IDSs and firewalls behind the host generally queue all of them and process them one by one. However, since this method of processing involves greater CPU consumption as well as network resources, the configuration of most of IDSs makes it skip fragmented packets during port scans.

nmap -g 80 [Target IP Address]
- In this command, you can use the -g or --source-port option to perform source port manipulation.
    > Source port manipulation refers to manipulating actual port numbers with common port numbers to evade IDS/firewall: this is useful when the firewall is configured to allow packets from well-known ports like HTTP, DNS, FTP, etc.

nmap -mtu 8 [Target IP Address]
- In this command, -mtu: specifies the number of Maximum Transmission Unit (MTU) (here, 8 bytes of packets).
    > Using MTU, smaller packets are transmitted instead of sending one complete packet at a time. This technique evades the filtering and detection mechanism enabled in the target machine.

nmap -D RND:10 [Target IP Address]
- In this command, -D: performs a decoy scan and RND: generates a random and non-reserved IP addresses (here, 10).
    > The IP address decoy technique refers to generating or manually specifying IP addresses of the decoys to evade IDS/firewall. This technique makes it difficult for the IDS/firewall to determine which IP address was actually scanning the network and which IP addresses were decoys. By using this command, Nmap automatically generates a random number of decoys for the scan and randomly positions the real IP address between the decoy IP addresses.

nmap -sT -Pn --spoof-mac 0 [Target IP Address]
- In this command --spoof-mac 0 represents randomizing the MAC address, -sT: performs the TCP connect/full open scan, -Pn is used to skip the host discovery.
    > MAC address spoofing technique involves spoofing a MAC address with the MAC address of a legitimate user on the network. This technique allows you to send request packets to the targeted machine/network pretending to be a legitimate host.

Create Custom UDP and TCP Packets using Hping3 to Scan beyond the IDS/Firewall
> Hping3 is a scriptable program that uses the TCL language, whereby packets can be received and sent via a binary or string representation describing the packets.

hping3 [Target IP Address] --udp --rand-source --data 500
- Here, --udp specifies sending the UDP packets to the target host, --rand-source enables the random source mode and --data specifies the packet body size.

hping3 -S [Target IP Address] -p 80 -c 5
- Here, -S specifies the TCP SYN request on the target machine, -p specifies assigning the port to send the traffic, and -c is the count of the packets sent to the target machine.

hping3 [Target IP Address] --flood
- --flood: performs the TCP flooding.

Scan a Target Network using Metasploit:
> Metasploit Framework is a tool that provides information about security vulnerabilities in the target organization’s system, and aids in penetration testing and IDS signature development. It facilitates the tasks of attackers, exploit writers, and payload writers. A major advantage of the framework is the modular approach, that is, allowing the combination of any exploit with any payload.

```
service postgresql start
msfdb init
msfconsole 

db_status 

nmap -Pn -sS -A -oX Test 10.10.1.0/24

db_import Test

hosts 

db_services 

use auxiliary/scanner/portscan/syn

set INTERFACE eth0
set PORTS 80
set RHOSTS 10.10.1.5-23
set THREADS 50

run


use auxiliary/scanner/portscan/tcp

set RHOSTS [Target IP Address]

run


use auxiliary/scanner/smb/smb_version

set RHOSTS 10.10.1.5-23

set THREADS 11

```







