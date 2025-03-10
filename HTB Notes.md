[[Pentesting Toolset]]
# Module 3 ( Getting Started )
- [x] [[Cron]]
- [x] [[Privilege Escalation]]
- [ ] [[Information Security (InfoSec)]]
- [ ] [[Confidentiality, Integrity, and Availability Triad (CIA Triad)]]
- [ ] [[Risk Management Process]]
- [ ] [[Red Team VS Blue Team]]
- [ ] [[Parrot OS]]
- [ ] [[Pwn]]
- [ ] [[Hyper-V]]
- [ ] [[Hypervisor]]
- [ ] [[Optical disc image (ISO)]]
- [ ] [[Open Virtual Appliance (OVA)]]
- [ ] [[Virtual Private Network (VPN)]]
- [ ] [[ifconfig.sh]]
- [ ] [[netstat.sh]]
- [ ] [[Bash]]
- [ ] [[Getting a Shell]]
- [ ] [[Port]]
- [ ] [[Open Web Application Security Project (OWASP)]]
- [ ] [[Secure Shell (SSH)]]
- [ ] [[nmap.sh]]
- [ ] [[File Transfer Protocol (FTP)]]
- [ ] [[ftp.sh]]
- [ ] [[Server Message Block (SMB)]]
- [ ] [[smbclient.sj]]
- [ ] [[Enumeraionj]]
- [ ]  [[gobuster.sh]]
- [ ] [[SecLists]]
- [ ] [[whatweb.sh]]
- [x] [[searchsploit.sh]]
- [x] [[Exploit Databases]]
- [x] [[metasploit.sh]]
---
```
It is common for websites to contain a `robots.txt` file, whose purpose is to instruct search engine web crawlers such as Googlebot which resources can and cannot be accessed for indexing. The `robots.txt` file can provide valuable information such as the location of private files and admin pages.
```

```sh
Projects/
└── Acme Company
    ├── EPT
    │   ├── evidence
    │   │   ├── credentials
    │   │   ├── data
    │   │   └── screenshots
    │   ├── logs
    │   ├── scans
    │   ├── scope
    │   └── tools
    └── IPT
        ├── evidence
        │   ├── credentials
        │   ├── data
        │   └── screenshots
        ├── logs
        ├── scans
        ├── scope
        └── tools
#Acme is the company we're pentesting
#EPT -> External Pentesting
#IPT -> Internal Pentesting
```

```
NOTE: If you're using a notetaking software for penetrating a system, make sure it is only locally saved and not syncing to the cloud.
```

```
Using VPN services such NordVPN or ExpressVPN are not compeletly secure. since we are connecting to a company's server, there is always the chance that data is being logged or the VPN service is not following security best practices or the security features that they advertise. Usage of a VPN service does not guarantee anonymity or privacy. A VPN service should never be used with the thought that it will protect us from the consequences of performing nefarious activities.
```

```
When connected to HTB VPN (or any penetration testing/hacking-focused lab), we should always consider the network to be "hostile." We should only connect from a virtual machine, disallow password authentication if SSH is enabled on our attacking VM, lockdown any web servers, and not leave sensitive information on our attack VM
```

```
It is essential for us, especially as pentesters, to have a firm grasp of many `TCP` and `UDP` ports and be able to recognize them from just their number quickly (i.e., know that port `21` is `FTP`, port `80` is `HTTP`, port `88` is `Kerberos`) without having to look it up.
```

```
Web application security assessment methodologies are often based around the OWASP top 10 as a starting point for the top categories of flaws that an assessor should be checking for. The current OWASP Top 10 list is:
```

```
A service is an application running on a computer that performs some useful function for other users or computers. We call these specialized machines that host these useful services "servers" instead of workstations, allowing users to interact with and consume these various services.
```

```
As we gain familiarity, we will notice that several ports are commonly associated with Windows or Linux. For example, port 3389 is the default port for Remote Desktop Services and is an excellent indication that the target is a Windows machine. In our current scenario, port 22 (SSH) being available indicates that the target is running Linux/Unix, but this service can also be configured on Windows.
```
# Module 2 ( JavaScript Deobfuscation)
[[Hypertext Markup Language (HTML)]]
[[Cascading Style Sheets (CSS)]]
[[Javascript]]
[[Code Obfuscation]]
[[Code Deobfuscation]]
[[Code Minification]]
[[Hex Encoding]]
[[base64.sh]]
[[xxd.sh]]
```
CTRL+u -> Show HTML source code (Chrome/Firefox)
```

```
NOTE: Base64 encoded strings can be easily spotted with a = at the end.
```

```
NOTE: There is no ROT13 command in linux but you can achieve the same thing with:
echo "text before encoding" | tr 'A-Za-z' 'N-ZA-Mn-za-m'

PS: The same command decodes ROT13
```
### Tools
- [cipher identifer to identify what type of encoding is used](https://www.boxentriq.com/code-breaking/cipher-identifier)
# Module 1 ( Web Requests)
```
Note: Our browsers usually first look up records in the local '`/etc/hosts`' file, and if the requested domain does not exist within it, then they would contact other DNS servers. We can use the '`/etc/hosts`' to manually add records to for DNS resolution, by adding the IP followed by the domain name.
```

```
By default, servers are configured to return an index file when a request for `/` is received. in this case, the contents of `index.html` are read and returned by the web server as an HTTP response.
```

```
Note: Although the data transferred through the HTTPS protocol may be encrypted, the request may still reveal the visited URL if it contacted a clear-text DNS server. For this reason, it is recommended to utilize encrypted DNS servers (e.g. 8.8.8.8 or 1.1.1.1), or utilize a VPN service to ensure all traffic is properly encrypted.
```

```
Note: HTTP version 1.X sends requests as clear-text, and uses a new-line character to separate different fields and different requests. HTTP version 2.X, on the other hand, sends requests as binary data in a dictionary form.
```

```
Note: Most modern web applications mainly rely on the `GET` and `POST` methods. However, any web application that utilizes REST APIs also rely on `PUT` and `DELETE`, which are used to update and delete data on the API endpoint, respectively.
```

```
Note: The HTTP `PATCH` method may also be used to update API entries instead of `PUT`. To be precise, `PATCH` is used to partially update an entry (only modify some of its data "e.g. only city_name"), while `PUT` is used to update the entire entry. We may also use the HTTP `OPTIONS` method to see which of the two is accepted by the server, and then use the appropriate method accordingly.
```
---
https://www.youtube.com/watch?v=S6uYZ8V1vRc&ab_channel=TechTerms
---
[[OpenVPN]]
[[Hypertext Transfer Protocol (HTTP)|HTTP]]
[[Domain Name System (DNS)]]
[[Domain Name]]
[[DNS Record]]
[[DNS resolver]]
[[Hostname]]
[[Fully Qualified Domain Name (FQDN)]]
[[Uniform Resource Locator (URL)]]
[[Internet Protocol address (IP address)|IP addresses]]
[[Internet Service Provider (ISP)]]
[[Hypertext Transfer Protocol (HTTP)|HTTP]]
[[Hypertext Transfer Protocol Secure (HTTPS)|HTTPS]]
[[curl.sh]]
[[Man In The Middle (MITM)]]
[[HTTP Request]]
[[HTTP Response]]
[[HTTP Basic Authentication]]
[[Application Programming Interface (API)]]
[[CRUD API]]
[[jq.sh]]