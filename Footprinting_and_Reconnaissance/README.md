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




