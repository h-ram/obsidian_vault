#command

Nmap (**Network Mapper**) is an open-source **network scanning** tool.
```bash
	nmap [options] target
```

> [!info] Note
> The default nmap command will only scan the common ports (1-1023) using TCP
# **Possible Target Values in Nmap**
### **1. Single Host**

|Target Format|Example|Description|
|---|---|---|
|IP Address|`nmap 192.168.1.1`|Scan a single IP|
|Hostname|`nmap example.com`|Scan a domain name (resolves to IP)|
### **2. Multiple Hosts**

|Target Format|Example|Description|
|---|---|---|
|Space-separated IPs|`nmap 192.168.1.1 192.168.1.2`|Scan multiple specific hosts|
|Comma-separated|`nmap 192.168.1.1,192.168.1.2`|Alternative format for multiple hosts|
|Hostname List|`nmap example.com google.com`|Scan multiple domains|
### **3. IP Ranges**

|Target Format|Example|Description|
|---|---|---|
|CIDR Notation|`nmap 192.168.1.0/24`|Scan a subnet (256 hosts)|
|Dash Range|`nmap 192.168.1.1-100`|Scan a range of IPs|
|Mixed CIDR & Single|`nmap 10.0.0.1,192.168.1.0/24`|Scan multiple targets together|
### **4. Reading Targets from a File**

|Target Format|Example|Description|
|---|---|---|
|File Input|`nmap -iL targets.txt`|Read multiple targets from a file (one per line)|
**Example `targets.txt` content:**
```
192.168.1.1
192.168.1.10-20
example.com
```

---
### **5. Random Hosts**

|Target Format|Example|Description|
|---|---|---|
|Random Scan|`nmap -iR 10`|Scan 10 random public IPs|

---

### **6. IPv6 Scanning**

|Target Format|Example|Description|
|---|---|---|
|IPv6|`nmap -6 2001:db8::1`|Scan a single IPv6 address|
|IPv6 Subnet|`nmap -6 2001:db8::/64`|Scan an IPv6 subnet|

---

### **7. Excluding Targets**

|Target Format|Example|Description|
|---|---|---|
|Exclude Hosts|`nmap 192.168.1.0/24 --exclude 192.168.1.1`|Scan a subnet but exclude a specific host|
|Exclude from File|`nmap 192.168.1.0/24 --excludefile exclude.txt`|Read exclusions from a file|

**Example `exclude.txt` content:**

```
192.168.1.1
192.168.1.5
example.com
```

---

# **Options**

| **Option**       | **Meaning**                                                                                     |
| ---------------- | ----------------------------------------------------------------------------------------------- |
| `-sn`            | **Ping Scan Only** (Checks which hosts are up without scanning ports)                           |
| `-p`             | **Port Specification** (Allows scanning specific ports, e.g., `-p 80,443`)                      |
| `-p-`            | **Full Port Scan** (Scans all 65,535 ports)                                                     |
| `-Pn`            | **Disable Host Discovery** (Assumes all hosts are online and scans directly)                    |
| `-sV`            | **Service Version Detection** (Identifies service versions on open ports)                       |
| `-O`             | **OS Detection** (Attempts to determine the target OS)                                          |
| `-sS`            | **SYN Scan** (Stealth scan that doesn’t complete TCP handshake)                                 |
| `-sT`            | **TCP Connect Scan** (Full connection scan, noisier than SYN scan)                              |
| `-sU`            | **UDP Scan** (Scans open UDP ports)                                                             |
| `-A`             | **Aggressive Scan** (Enables OS detection, version detection, scripts, and traceroute)          |
| `-iL`            | **Input File for Targets** (Reads target hosts from a file)                                     |
| `-oN`            | **Normal Output** (Saves results in standard text format)                                       |
| `-oX`            | **XML Output** (Saves results in XML format)                                                    |
| `--script`       | **NSE Script Execution** (Runs Nmap Scripting Engine scripts for vulnerability detection, etc.) |
| `--open`         | **Show Only Open Ports** (Filters results to display only open ports)                           |
| `--max-retries`  | **Limit Retries** (Sets the maximum number of times Nmap retries a probe)                       |
| `--min-rate`     | **Set Minimum Scan Rate** (Controls the number of packets sent per second)                      |
| `--max-rate`     | **Set Maximum Scan Rate** (Limits the number of packets sent per second)                        |
| `--host-timeout` | **Limit Scan Time per Host** (Stops scanning a host if it takes too long)                       |
| `--scan-delay`   | **Set Delay Between Probes** (Controls the time gap between sending scan packets)               |
# **Usage**
### **Ping Scan**
Checks which hosts are **up** without scanning ports.
```bash
$ nmap -sn --open 192.168.1.0/24 | grep "scan report"
Starting Nmap at 2025-02-20 07:11 CET
Nmap scan report for 192.168.1.1
Host is up (0.0019s latency).
Nmap scan report for 192.168.1.6
Host is up (0.012s latency).
Nmap scan report for 192.168.1.7
Nmap done: 256 IP addresses (3 hosts up) scanned in 18.60 seconds

$ nmap -sn --open 192.168.1.0/24 | grep "scan report"
Nmap scan report for 192.168.1.1
Nmap scan report for 192.168.1.6
Nmap scan report for 192.168.1.7
```

```bash
# Scan a single host
nmap 192.168.1.1

# Scan a Subnet (Multiple Hosts)
nmap 192.168.1.0/24

# Scan a Specific Port
nmap -p 80 192.168.1.1

# Scan Multiple Ports
nmap -p 22,80,443 192.168.1.1

# Scan All 65,536 Ports
nmap -p- 192.168.1.1

# Detect Service Version
nmap -sV 192.168.1.1

# Detect Operating System
nmap -O 192.168.1.1

# Enable Nmap Scripting Engine (NSE) default scripts
namp -sC 192.168.1.1
```
---
### **Nmap Scripts**
Specifying `-sC` will run many useful default scripts against a target, but there are cases when running a specific script is required.
```bash
nmap --script <script name> -p<port> <host>
```
You can find the scripts using [[locate.sh]]
```bash
$ locate nmap/scripts/citrix
/usr/share/nmap/scripts/citrix-brute-xml.nse
/usr/share/nmap/scripts/citrix-enum-apps-xml.nse
/usr/share/nmap/scripts/citrix-enum-apps.nse
/usr/share/nmap/scripts/citrix-enum-servers-xml.nse
/usr/share/nmap/scripts/citrix-enum-servers.nse
```

# **Installation**
```bash
sudo pacman -S nmap
sudo apt install nmap -y
sudo dnf install nmap -y
sudo zypper install nmap
brew install nmap
choco install nmap
scoop install nmap
```