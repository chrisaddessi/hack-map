# Map Construction Of Target
The purpose of this step is to gain information about the Domain. Such as: <br />
Owner info <br />
subdomains <br />
Cloud hosted?


## DNS & Subdomain Enumeration Tools
### amass
https://github.com/OWASP/Amass <br />
Performs network mapping of attack surfaces and external asset discovery using open source information gathering and active reconnaissance techniques. <br />
amass has many sub-commands <br />
subdomain enumeration
```bash
amass enum -v -src -ip -brute -min-for-recursive 2 -d zonetransfer.me -dir outfolder # subdomain brute forceing
amass enum -d somesub.someschool.edu -dir somesub.someschool.edu-result
amass enum -d zonetransfer.me -src -ip -dir zonetransfer-output #gets IPs and sources
```
simple intel scan
```bash
amass intel -whois -d zonetransfer.me -dir zonetransfer-result
```
viz sub-command <br />
creates a vizual graph
```
amass db -dir zonetransfer-out -list #list reports
amass viz -dir zonetransfer-out -d3 #d3 is format
#go open the file outputed in browser
```
### dimtry
gives ip like a whois
```bash
dmitry -o dmitryscan list.wordpress.org
```
### fierce
A subdomain brute forcing tool. It is very active.
```bash
fierce --domain zontransfer.me 
fierce --domain zontransfer.me --subdomains 
```
### knockpy
subdomain brute force 
### dnsdumpster.com
### dnsrecon
Enumerate SRV, MX, SOA, NS, A, AAAA, SPF, TXT. Brute Force subdomain. Enumerate Hosts and Subdomains using Google
### wfw00f
### whois
### netcraft
### whatweb
### dig
### dnsenum
### gobuster
use vhosts if you cant find any on dns option
```bash
gobuster vhost -h
gobuster dns -h
```
### Google dorking technquies
This search gets subdomains of bbc.com that google has indexed, while also removing results for the main site www.bbc.com
```
site:*.bbc.com -site:www.bbc.com
```

### websites
dnsdumpster.com
arinwhois

### Google Dorking
```
site:*.bbc.com -site:www.bbc.com
```
## Two Paths
If the server appears to be running on a service like cloudflare or aws going further with nmap will not necessarily be helpful as many ports are open. Cloud hosting servers often come with firewalls. 

If the server does not seem to be hosted on cloudflare for example. Use path A. Otherwis use path B.
### Path A
[PathA](https://github.com/chrisaddessi/hack-map/tree/main/attack-for-root/A)
### Path B
[PathB](https://github.com/chrisaddessi/hack-map/tree/main/attack-for-root/standard)
