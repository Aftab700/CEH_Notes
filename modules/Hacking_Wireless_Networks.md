# Hacking Wireless Networks 
> A wireless network is an unbounded data communication system that uses radio-frequency technology to communicate with devices and obtain data. Through radio frequency technology, Wi-Fi allows devices to access wireless networks without cables from anywhere within range of an access point. The wireless network can be at risk to various types of attacks, including access-control attacks, integrity attacks, confidentiality attacks, availability attacks, and authentication attacks.


Overview of Wireless Networking:
- In wireless networks, communication takes place through radio wave transmission, which usually takes place at the physical layer of the network structure. Thanks to the wireless communication revolution, fundamental changes to data networking and telecommunication are taking place. This means that you will need to know and understand several types of wireless networks. These include:
  - Extension to a wired network: A wired network is extended by the introduction of access points between the wired network and wireless devices
  - Multiple access points: Multiple access points connect computers wirelessly
  - LAN-to-LAN wireless network: All hardware APs have the ability to interconnect with other hardware access points
  - 3G/4G hotspot: A mobile device shares its cellular data wirelessly with Wi-Fi-enabled devices such as MP3 players, notebooks, tablets, cameras, PDAs, and netbooks


Overview of Wireless Traffic Analysis:
- Wireless traffic analysis helps in determining the appropriate strategy for a successful attack. Wi-Fi protocols are unique at Layer 2, and traffic over the air is not serialized, which makes it easy to sniff and analyze wireless packets. You can use various Wi-Fi packet-sniffing tools to capture and analyze the traffic of a target wireless network.


There are several different types of Wi-Fi attacks that attackers use to eavesdrop on wireless network connections in order to obtain sensitive information such as passwords, banking credentials, and medical records, as well as to spread malware.

These include:
- Fragmentation attack: When successful, such attacks can obtain 1,500 bytes of PRGA (pseudo random generation algorithm)
- MAC spoofing attack: The attacker changes their MAC address to that of an authenticated user in order to bypass the access point’s MAC-filtering configuration
- Disassociation attack: The attacker makes the victim unavailable to other wireless devices by destroying the connectivity between the access point and client
- Deauthentication attack: The attacker floods station(s) with forged deauthentication packets to disconnect users from an access point
- Man-in-the-middle attack: An active Internet attack in which the attacker attempts to intercept, read, or alter information between two computers
- Wireless ARP poisoning attack: An attack technique that exploits the lack of a verification mechanism in the ARP protocol by corrupting the ARP cache maintained by the OS in order to associate the attacker’s MAC address with the target host
- Rogue access points: Wireless access points that an attacker installs on a network without authorization and that are not under the management of the network administrator
- Evil twin: A fraudulent wireless access point that pretends to be a legitimate access point by imitating another network name
- Wi-Jacking attack: A method used by attackers to gain access to an enormous number of wireless networks


Crack a WEP network using Aircrack-ng:
- Aircrack-ng is a network software suite consisting of a detector, packet sniffer, WEP, and WPA/WPA2-PSK cracker and analysis tool for 802.11 wireless networks. The program runs on both Linux and Windows.
- `aircrack-ng '/home/attacker/Desktop/Sample Captures/WEPcrack-01.cap' `


Crack a WPA2 Network using Aircrack-ng:
- WPA2 is an upgrade to WPA; it includes mandatory support for Counter Mode with Cipher Block Chaining Message Authentication Code Protocol (CCMP), an AES-based encryption protocol with strong security. WPA2 has two modes of operation: WPA2-Personal and WPA2-Enterprise. Despite being stronger than both WEP and WPA, the WPA2 encryption method can also be cracked using various techniques and tools.

- `aircrack-ng -a2 -b [Target BSSID] -w /home/attacker/Desktop/Wordlist/password.txt '/home/attacker/Desktop/Sample Captures/WPA2crack-01.cap' `
  - -a is the technique used to crack the handshake, 2=WPA technique.
  - -b refers to bssid; replace with the BSSID of the target router.
  - -w stands for wordlist; provide the path to a wordlist.


------

-> Decrypt wifi traffic: Wireshark > Edit > Preference > Protocol > IEEE 802.11 > add WPA keys(password)







