# Session Hijacking
> Session hijacking is when an attacker takes over either a valid TCP communication session between two computers or a valid user session in a web application.


A session hijacking attack refers to the exploitation of a session token-generation mechanism or token security controls that enables an attacker to establish an unauthorized connection with a target server. The attacker guesses or steals a valid session ID (which identifies authenticated users) and uses it to establish a session with the server.

- Active session hijacking: An attacker finds an active session and takes it over
- Passive session hijacking: An attacker hijacks a session, and, instead of taking over, monitors and records all the traffic in that session


Session hijacking can be divided into three broad phases:
- Tracking the Connection: The attacker uses a network sniffer to track a victim and host, or uses a tool such as Nmap to scan the network for a target with a TCP sequence that is easy to predict
- Desynchronizing the Connection: A desynchronized state occurs when a connection between the target and host has been established, or is stable with no data transmission, or when the server’s sequence number is not equal to the client’s acknowledgment number (or vice versa)
- Injecting the Attacker’s Packet: Once the attacker has interrupted the connection between the server and target, they can either inject data into the network or actively participate as the man-in-the-middle, passing data between the target and server, while reading and injecting data at will


There are two primary methods that can be used to detect session hijacking:
- Manual Method: Involves using packet sniffing software such as Wireshark and SteelCentral Packet Analyzer to monitor session hijacking attacks; the packet sniffer captures packets being transferred across the network, which are then analyzed using various filtering tools
- Automatic Method: Involves using Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS) to monitor incoming network traffic; if a packet matches any of the attack signatures in the internal database, the IDS generates an alert, and the IPS blocks the traffic from entering the database









































