# Footprinting and Reconnaissance

> Footprinting refers to collecting as much information as possible regarding a target network from publicly accessible sources.

<br>

## Perform Footprinting Through Search Engines

https://mattw.io/youtube-metadata/
> YouTube Metadata tool collects singular details of a video, its uploader, playlist and its creator or channel.

[TinEye Reverse Image Search](https://tineye.com)

FTP Search Engines:
- https://www.searchftps.net/ 
- https://www.freewareweb.com/

IoT Search Engines:
- https://www.shodan.io/
- https://search.censys.io/

Domains and Sub-domains:
- https://www.netcraft.com/tools/
- https://github.com/aboul3la/Sublist3r

theHarvester:
> This tool gathers emails, subdomains, hosts, employee names, open ports, and banners from different public sources such as search engines, PGP key servers, and the SHODAN computer database as well as uses Google, Bing, SHODAN, etc.
```
theHarvester -d eccouncil -l 200 -b linkedin
```
> -d specifies the domain or company name to search (here, eccouncil), -l specifies the number of results to be retrieved, and -b specifies the data source as LinkedIn.

Deep and Dark Web Searching:
- [The Hidden Wiki](http://zqktlwiuavvvqqt4ybvgvi7tyo4hjl5xgfuvpdf6otjiycgwqbym2qad.onion/wiki)
- [FakeID](http://ymvhtqya23wqpez63gyc3ke4svju3mqsby2awnhd3bk2e65izt7baqad.onion) is an onion site for creating fake passports
- [Cardshop](http://s57divisqlcjtsyutxjz2ww77vlbwpxgodtijcsrgsuts4js5hnxkhqd.onion) is an onion site that sells cards with good balances
- [ExoneraTor](https://metrics.torproject.org)
- [OnionLand Search engine](https://onionlandsearchengine.com),

Information from Various Social Networking Sites:
- [Sherlock](https://github.com/sherlock-project/sherlock):
    > Sherlock is a python-based tool that is used to gather information about a target person over various social networking sites. Sherlock searches a vast number of social networking sites for a given target user, locates the person, and displays the results along with the complete URL related to the target person.
- [Social Searcher](https://www.social-searcher.com/)
- [Followerwonk](https://followerwonk.com/analyze)
    > Followerwonk is an online tool that helps you explore and grow your social graph, digging deeper into Twitter analytics; for example, Who are your followers? Where are they located? When do they tweet? This can be used to gather Twitter information about any target organization or individual.

Gather Information about a Target Website:
- [Photon](https://github.com/s0md3v/Photon)
   > Photon is a Python script used to crawl a given target URL to obtain information such as URLs (in-scope and out-of-scope), URLs with parameters, email addresses, social media accounts, files, secret keys and subdomains. The extracted information can further be exported in the JSON format.

- [Central Ops](https://centralops.net/co/)
    > CentralOps (centralops.net) is a free online network scanner that investigates domains and IP addresses, DNS records, traceroute, nslookup, whois searches, etc.

- https://github.com/digininja/CeWL
- https://whois.domaintools.com/

DNS Footprinting
- nslookup 
- http://www.kloth.net/services/nslookup.php
- https://dnsdumpster.com/
- https://www.broadbandsearch.net/network-tools
- https://www.yougetsignal.com/
- https://securitytrails.com/

Locate the Network Range

- tracert   <-- windows 
- traceroute    <-- linux

Recon-ng:
> Recon-ng is a web reconnaissance framework with independent modules and database interaction that provides an environment in which open-source web-based reconnaissance can be conducted. Here, we will use Recon-ng to perform network reconnaissance, gather personnel information, and gather target information from social networking sites.

Maltego:
> Maltego is a footprinting tool used to gather maximum information for the purpose of ethical hacking, computer forensics, and pentesting. It provides a library of transforms to discover data from open sources and visualizes that information in a graph format, suitable for link analysis and data mining. Maltego provides you with a graphical interface that makes seeing these relationships instant and accurate, and even making it possible to see hidden connections.

OSRFramework:
> OSRFramework is a set of libraries that are used to perform Open Source Intelligence tasks. They include references to many different applications related to username checking, DNS lookups, information leaks research, deep web search, regular expressions extraction, and many others. It also provides a way of making these queries graphically as well as several interfaces to interact with such as OSRFConsole or a Web interface.

domainfy :
- `domainfy -n [Domain Name] -t all `
-   > -n: specifies a nickname or a list of nicknames to be checked. -t: specifies a list of top-level domains where nickname will be searched.

searchfy:
> check for the existence of a given user details on different social networking platforms such as Github, Instagram and Keyserverubuntu. Type searchfy -q "target user name or profile name"

BillCipher:
> BillCipher is an information gathering tool for a Website or IP address. Using this tool, you can gather information such as DNS Lookup, Whois lookup, GeoIP Lookup, Subnet Lookup, Port Scanner, Page Links, Zone Transfer, HTTP Header, etc. Here, we will use the BillCipher tool to footprint a target website URL.


### OSINT Framework:

- https://osintframework.com/



