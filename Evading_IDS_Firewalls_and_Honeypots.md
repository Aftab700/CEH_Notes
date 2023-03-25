# Evading IDS, Firewalls, and Honeypots
> Evading IDS and firewalls involves modifying attacks to escape detection by an organization’s security systems, whereas honeypots are traps set to detect, deflect, or counteract unauthorized intrusion attempts.


IDSs, which provide an extra layer of security to the organization’s infrastructure, are attractive targets for attackers. Attackers implement various IDS evasion techniques to bypass this security mechanism and compromise the infrastructure. Many IDS evasion techniques circumvent detect detection through multiple methods and can adapt to the best possible method for each system.


The firewall operates on a predefined set of rules. Using extensive knowledge and skill, an attacker can bypass the firewall by employing various bypassing techniques. Using these techniques, the attacker tricks the firewall to not filter the generated malicious traffic.


 Intrusion Detection Systems:
- Intrusion detection systems are highly useful as they monitor both the inbound and outbound traffic of the network and continuously inspects the data for suspicious activities that may indicate a network or system security breach. The IDS checks traffic for signatures that match known intrusion patterns and signals an alarm when a match is detected. It can be categorized into active and passive, depending on its functionality: an IDS is generally passive and is used to detect intrusions, while an intrusion prevention system (IPS) is considered as an active IDS, as it is not only used to detect the intrusion on the network, but also prevent them.
- Main Functions of IDS:
  - Gathers and analyzes information from within a computer or a network, to identify the possible violations of security policy
  - Also referred to as a “packet-sniffer,” which intercepts packets traveling along various communication mediums and protocols
  - Evaluates traffic for suspected intrusions and signals an alarm after detection


Detect Intrusions using Snort:
- Snort is an open-source network intrusion detection system, capable of performing real-time traffic analysis and packet logging on IP networks. It can perform protocol analysis and content searching/matching and is used to detect a variety of attacks and probes such as buffer overflows, stealth port scans, CGI attacks, SMB probes, and OS fingerprinting attempts. It uses a flexible rules language to describe traffic to collect or pass, as well as a detection engine that utilizes a modular plug-in architecture.
- Uses of Snort:
  - Straight packet sniffer such as tcpdump
  - Packet logger (useful for network traffic debugging, etc.)
  - Network intrusion prevention system


Detect Malicious Network Traffic using ZoneAlarm FREE FIREWALL:
- ZoneAlarm FREE Firewall blocks attackers and intruders from accessing your system. It manages and monitors all incoming and outgoing traffic and shields the network from hackers, malware, and other online threats that put network privacy at risk, and monitors programs for suspicious behavior spotting and stopping new attacks that bypass traditional anti-virus protection. This Firewall prevents identity theft by guarding your data, and erases your tracks allowing you to surf the web in complete privacy. Furthermore, it locks out attackers, blocks intrusions, and makes your PC invisible online. Additionally, it filters out annoying, as well as potentially dangerous, email.


Detect Malicious Network Traffic using HoneyBOT:
- HoneyBOT is a medium interaction honeypot for windows. A honeypot creates a safe environment to capture and interact with unsolicited traffic on a network. HoneyBOT is an easy-to-use solution that is ideal for network security research or as part of an early-warning IDS.


Firewalls Evasion Techniques:
- A firewall operates on a predefined set of rules. Using extensive knowledge and skill, an attacker can bypass the firewall by employing various bypassing techniques. Using these techniques, the attacker tricks the firewall to not filter the malicious traffic that he/she generates.
- The following are some firewall bypassing techniques
  - Port Scanning
  - Firewalking
  - Banner Grabbing
  - IP Address Spoofing
  - Source Routing
  - Tiny Fragments
  - Using an IP Address in Place of URL
  - Using Anonymous Website Surfing Sites
  - Using a Proxy Server
  - ICMP Tunneling
  - ACK Tunneling
  - HTTP Tunneling
  - SSH Tunneling
  - DNS Tunneling
  - Through External Systems
  - Through MITM Attack
  - Through Content
  - Through XSS Attack








































































