# Denial-of-Service
> Denial-of-Service is an attack on a computer or network that reduces, restricts, or prevents accessibility of system resources to its legitimate users.


Denial of Service:
- A DoS attack is a type of security break that does not generally result in the theft of information. However, these attacks can harm the target in terms of time and resources. Further, failure to protect against such attacks might mean the loss of a service such as email. In a worst-case scenario, a DoS attack can mean the accidental destruction of the files and programs of millions of people who happen to be surfing the Web at the time of the attack.
- Some examples of types of DoS attacks:
  - Flooding the victim’s system with more traffic than it can handle
  - Flooding a service (such as an internet relay chat (IRC)) with more events than it can handle
  - Crashing a transmission control protocol (TCP)/internet protocol (IP) stack by sending corrupt packets
  - Crashing a service by interacting with it in an unexpected way
  - Hanging a system by causing it to go into an infinite loop


DoS and DDoS attacks have become popular, because of the easy accessibility of exploit plans and the negligible amount of brainwork required while executing them. These attacks can be very dangerous, because they can quickly consume the largest hosts on the Internet, rendering them useless. The impact of these attacks includes loss of goodwill, disabled networks, financial loss, and disabled organizations.


DoS and DDoS Attacks:
- DDoS attacks mainly aim at the network bandwidth; they exhaust network, application, or service resources, and thereby restrict legitimate users from accessing their system or network resources.

In general, the following are categories of DoS/DDoS attack vectors:
- Volumetric Attacks: Consume the bandwidth of the target network or service
- Attack techniques:
  - UDP flood attack
  - ICMP flood attack
  - Ping of Death and smurf attack
  - Pulse wave and zero-day attack
- Protocol Attacks: Consume resources like connection state tables present in the network infrastructure components such as load-balancers, firewalls, and application servers
- Attack techniques:
  - SYN flood attack
  - Fragmentation attack
  - Spoofed session flood attack
  - ACK flood attack

- Application Layer Attacks: Consume application resources or services, thereby making them unavailable to other legitimate users
- Attack techniques:
  - HTTP GET/POST attack
  - Slowloris attack
  - UDP application layer flood attack
  - DDoS extortion attack


DoS Attack (SYN Flooding):
- SYN flooding takes advantage of a flaw with regard to how most hosts implement the TCP three-way handshake. This attack occurs when the intruder sends unlimited SYN packets (requests) to the host system. The process of transmitting such packets is faster than the system can handle. Normally, the connection establishes with the TCP three-way handshake, and the host keeps track of the partially open connections while waiting in a listening queue for response ACK packets.


Perform a DoS Attack using Raven-storm:
- Raven-Storm is a DDoS tool for penetration testing that features Layer 3, Layer 4, and Layer 7 attacks. It is written in python3 and is effective and powerful in shutting down hosts and servers. It can be used to perform strong attacks and can be optimized for non typical targets.


Perform a DDoS Attack using HOIC:
- HOIC (High Orbit Ion Cannon) is a network stress and DoS/DDoS attack application. This tool is written in the BASIC language. It is designed to attack up to 256 target URLs simultaneously. It sends HTTP, POST, and GET requests to a computer that uses lulz inspired GUIs. It offers a high-speed multi-threaded HTTP Flood; a built-in scripting system allows the deployment of “boosters,” which are scripts designed to thwart DDoS countermeasures and increase DoS output.


Perform a DDoS Attack using LOIC:
- LOIC (Low Orbit Ion Cannon) is a network stress testing and DoS attack application. We can also call it an application-based DOS attack as it mostly targets web applications. We can use LOIC on a target site to flood the server with TCP packets, UDP packets, or HTTP requests with the intention of disrupting the service of a particular host.

<br>

DoS and DDoS Attack Detection:
- Detection techniques are based on identifying and discriminating the illegitimate traffic increase and flash events from the legitimate packet traffic.

The following are the three types of detection techniques:
- Activity Profiling: Profiles based on the average packet rate for a network flow, which consists of consecutive packets with similar packet header information
- Sequential Change-point Detection: Filters network traffic by IP addresses, targeted port numbers, and communication protocols used, and stores the traffic flow data in a graph that shows the traffic flow rate over time
- Wavelet-based Signal Analysis: Analyzes network traffic in terms of spectral components



Detect and Protect Against DDoS Attacks using Anti DDoS Guardian:
- Anti DDoS Guardian is a DDoS attack protection tool. It protects IIS servers, Apache serves, game servers, Camfrog servers, mail servers, FTP servers, VOIP PBX, and SIP servers and other systems. Anti DDoS Guardian monitors each incoming and outgoing packet in Real-Time. It displays the local address, remote address, and other information of each network flow. Anti DDoS Guardian limits network flow number, client bandwidth, client concurrent TCP connection number, and TCP connection rate. It also limits the UDP bandwidth, UDP connection rate, and UDP packet rate.




















