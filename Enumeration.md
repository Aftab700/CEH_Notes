# Enumeration
> Enumeration is the process of extracting usernames, machine names, network resources, shares, and services from a system or network.

<br>

NetBIOS Enumeration:
> NetBIOS stands for Network Basic Input Output System. Windows uses NetBIOS for file and printer sharing. A NetBIOS name is a unique computer name assigned to Windows systems, comprising a 16-character ASCII string that identifies the network device over TCP/IP. The first 15 characters are used for the device name, and the 16th is reserved for the service or name record type.

- nbtstat -a [IP address of the remote machine] 
    - In this command, -a displays the NetBIOS name table of a remote computer.
-  nbtstat -c
    -  In this command, -c lists the contents of the NetBIOS name cache of the remote computer.
- nmap -sV -v --script nbstat.nse [Target IP Address]
    - -sV detects the service versions, -v enables the verbose output (that is, includes all hosts and ports in the output), and --script nbstat.nse performs the NetBIOS enumeration.
    - nmap -sU -p 137 --script nbstat.nse

Overview of SNMP Enumeration:

> SNMP (Simple Network Management Protocol) is an application layer protocol that runs on UDP (User Datagram Protocol) and maintains and manages routers, hubs, and switches on an IP network. SNMP agents run on networking devices on Windows and UNIX networks.

> SNMP enumeration uses SNMP to create a list of the user accounts and devices on a target computer. SNMP employs two types of software components for communication: the SNMP agent and SNMP management station. The SNMP agent is located on the networking device, and the SNMP management station communicates with the agent.

SNMP uses port 161
- nmap -sU -p 161 [Target IP address]
    > -sU performs a UDP scan and -p specifies the port to be scanned. 

snmp-check [Target IP Address]

SnmpWalk:
> SnmpWalk is a command line tool that scans numerous SNMP nodes instantly and identifies a set of variables that are available for accessing the target network. It is issued to the root node so that the information from all the sub nodes such as routers and switches can be fetched.

- snmpwalk -v1 -c public [target IP]
    - –v: specifies the SNMP version number (1 or 2c or 3) and –c: sets a community string.
-  snmpwalk -v2c -c public [Target IP Address]
    -  –v: specifies the SNMP version (here, 2c is selected) and –c: sets a community string.

- nmap -sU -p 161 --script=snmp-sysdescr [target IP Address] 
    - -sU: specifies a UDP scan, -p: specifies the port to be scanned, and -–script: is an argument used to execute a given script (here, snmp-sysdescr).
- nmap -sU -p 161 --script=snmp-processes [target IP Address]
- nmap -sU -p 161 --script=snmp-win32-software [target IP Address]
- nmap -sU -p 161 --script=snmp-interfaces [target IP Address]

LDAP Enumeration:

> LDAP (Lightweight Directory Access Protocol) is an Internet protocol for accessing distributed directory services over a network. LDAP uses DNS (Domain Name System) for quick lookups and fast resolution of queries. A client starts an LDAP session by connecting to a DSA (Directory System Agent), typically on TCP port 389, and sends an operation request to the DSA, which then responds. BER (Basic Encoding Rules) is used to transmit information between the client and the server. One can anonymously query the LDAP service for sensitive information such as usernames, addresses, departmental details, and server names.

- nmap -sU -p 389 [Target IP address] 
- nmap -p 389 --script ldap-brute --script-args ldap.base='"cn=users,dc=CEH,dc=com"' [Target IP Address]
- ldapsearch
    - ldapsearch is a shell-accessible interface to the ldap_search_ext(3) library call. ldapsearch opens a connection to an LDAP server, binds the connection, and performs a search using the specified parameters. The filter should conform to the string representation for search filters as defined in RFC 4515. If not provided, the default filter, (objectClass=*), is used.
- ldapsearch -h [Target IP Address] -x -s base namingcontexts
    - -x: specifies simple authentication, -h: specifies the host, and -s: specifies the scope.
-  ldapsearch -h [Target IP Address] -x -b “DC=CEH,DC=com”
    -  -x: specifies simple authentication, -h: specifies the host, and -b: specifies the base DN for search.
-  ldapsearch -x -h [Target IP Address] -b "DC=CEH,DC=com" "objectclass=*" 
    -  -x: specifies simple authentication, -h: specifies the host, and -b: specifies the base DN for search.


NFS Enumeration:
> NFS (Network File System) is a type of file system that enables computer users to access, view, store, and update files over a remote server. This remote data can be accessed by the client computer in the same way that it is accessed on the local system.

- nmap -p 2049 [Target IP Address]
- https://github.com/p4pentest/SuperEnum
- https://github.com/hegusung/RPCScan

DNS Enumeration:
> DNS enumeration techniques are used to obtain information about the DNS servers and network infrastructure of the target organization. DNS enumeration can be performed using the following techniques:

- dig ns [Target Domain]
    - In this command, ns returns name servers in the result
- dig @[NameServer] [Target Domain] axfr 
    - (in this example, the name server is ns1.bluehost.com and the target domain is www.certifiedhacker.com); press Enter.
    - In this command, axfr retrieves zone information.

DNSSEC Zone Walking:
> DNSSEC zone walking is a DNS enumeration technique that is used to obtain the internal records of the target DNS server if the DNS zone is not properly configured. The enumerated zone information can assist you in building a host network map.

- ./dnsrecon.py -d [Target domain] -z
    - In this command, -d specifies the target domain and -z specifies that the DNSSEC zone walk be performed with standard enumeration.

- nmap --script=broadcast-dns-service-discovery [Target Domain]
- nmap -T4 -p 53 --script dns-brute [Target Domain] 
    - -T4: specifies the timing template, -p: specifies the target port.
- nmap --script dns-srv-enum --script-args "dns-srv-enum.domain='[Target Domain]'” 

SMTP Enumeration:
> The Simple Mail Transfer Protocol (SMTP) is an internet standard based communication protocol for electronic mail transmission. Mail systems commonly use SMTP with POP3 and IMAP, which enable users to save messages in the server mailbox and download them from the server when necessary. SMTP uses mail exchange (MX) servers to direct mail via DNS. It runs on TCP port 25, 2525, or 587.

- nmap -p 25 --script=smtp-enum-users [Target IP Address]
- nmap -p 25 --script=smtp-open-relay [Target IP Address] 
- nmap -p 25 --script=smtp-commands [Target IP Address] 

RPC Enumeration: Enumerating RPC endpoints enables vulnerable services on these service ports to be identified

SMB Enumeration: Enumerating SMB services enables banner grabbing, which obtains information such as OS details and versions of services running

FTP Enumeration: Enumerating FTP services yields information about port 21 and any running FTP services; this information can be used to launch various attacks such as FTP bounce, FTP brute force, and packet sniffing


Enumerate Information from Windows and Samba Hosts using Enum4linux:
- Enum4linux is a tool for enumerating information from Windows and Samba systems. It is used for share enumeration, password policy retrieval, identification of remote OSes, detecting if hosts are in a workgroup or a domain, user listing on hosts, listing group membership information, etc.
- enum4linux -u martin -p apple -n [Target IP Address]
- enum4linux -u martin -p apple -U [Target IP Address]
  - In this command, -u user specifies the username to use, -p pass specifies the password and -U retrieves the userlist.
  - -P retrieves the password policy information.
  - -o retrieves the OS information.
  -  -G retrieves group and member list.
  -  -S retrieves sharelist.









