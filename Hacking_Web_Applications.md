# Hacking Web Applications
> Hacking web applications refers to gaining unauthorized access to a website or its associated data.


Overview of Web Applications:
- Web applications provide an interface between end-users and web servers through a set of web pages generated at the server end or that contain script code to be executed dynamically in a client’s Web browser.
- Web applications run on web browsers and use a group of server-side scripts (such as ASP and PHP) and client-side scripts (such as HTML and JavaScript) to execute the application. The working of a web application depends on its architecture, which includes the hardware and software that performs tasks such as reading the request, searching, gathering, and displaying the required data.


Footprinting the web infrastructure allows attackers to engage in the following tasks:
- Server Discovery: Attackers attempt to discover the physical servers that host a web application using techniques such as Whois Lookup, DNS Interrogation, and Port Scanning
- Service Discovery: Attackers discover services running on web servers to determine whether they can use some of them as attack paths for hacking a web app
- Server Identification: Attackers use banner-grabbing to obtain server banners; this helps to identify the make and version of the web server software
- Hidden Content Discovery: Footprinting also allows attackers to extract content and functionality that is not directly linked to or reachable from the main visible content


Perform Web Application Reconnaissance using WhatWeb:
- WhatWeb identifies websites and recognizes web technologies, including content management systems (CMS), blogging platforms, statistics and analytics packages, JavaScript libraries, web servers, and embedded devices. It also identifies version numbers, email addresses, account IDs, web framework modules, SQL errors, and more.


Perform Web Spidering using OWASP ZAP:
- OWASP Zed Attack Proxy (ZAP) is an integrated penetration testing tool for finding vulnerabilities in web applications. It offers automated scanners as well as a set of tools that allow you to find security vulnerabilities manually. ZAP provides functionality for a range of skill levels—from developers to testers new to security testing, to security testing specialists.


Detect Load Balancers using Various Tools:
- Organizations use load balancers to distribute web server load over multiple servers and increase the productivity and reliability of web applications. Generally, there are two types of load balancers, namely, DNS load balancers (Layer 4 load balancers) and http load balancers (layer 7 load balancers). You can use various tools such as dig and load balancing detector (lbd) to detect the load balancers of the target organization along with their real IP addresses.


`gobuster dir -u [Target Website] -w /home/attacker/Desktop/common.txt`

`python3 dirsearch.py -u http://www.moviescope.com`

Identify XSS Vulnerabilities in Web Applications using PwnXSS:
- PwnXSS is an open-source XSS scanner that is used to detect cross-site scripting (XSS) vulnerabilities in websites. It is a multiprocessing and customizable tool written in Python language.
- ` python3 pwnxss.py -u http://testphp.vulnweb.com `


Perform Cross-site Request Forgery (CSRF) Attack:
- CSRF, also known as a one-click attack, occurs when a hacker instructs a user’s web browser to send a request to the vulnerable website through a malicious web page. Financial websites commonly contain CSRF vulnerabilities. Usually, outside attackers cannot access corporate intranets, so CSRF is one of the methods used to enter these networks. The inability of web applications to differentiate a request made using malicious code from a genuine request exposes it to the CSRF attack. These attacks exploit web page vulnerabilities that allow an attacker to force an unsuspecting user’s browser to send malicious requests that they did not intend.


`wpscan --api-token [API Token] --url http://10.10.1.22:8080/CEH --plugins-detection aggressive --enumerate vp `
- --enumerate vp: specifies the enumeration of vulnerable plugins.












