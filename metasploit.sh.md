#command 

An open-source pentesting framework used to identify, exploit, and validate vulnerabilities in systems, networks, and applications. it contains many built-in exploits for many public vulnerabilities.

```
msfconsole
```
---
# Usage
1. Run Metasploit
```bash
larry@arch $ msfconsole

[msf](Jobs:0 Agents:0) >>
```
2. Look for an exploit
```bash
[msf](Jobs:0 Agents:0) >> search exploit exploit_name

Matching Modules
================
 #  Name                 Disclosure Date  Rank     Check  Description
 -  ----                 ---------------  ----     -----  -----------
 0 exploit/exploit_name  2017-03-14       normal   Yes    User for something
```
3. `use` that exploit (either by its number or name)
```bash
[msf](Jobs:0 Agents:0) >> use 0
[msf](Jobs:0 Agents:0) auxiliary(exploit/exploit_name) >>
```
4. `show options` that you need to configure before running the exploit
```bash
[msf](Jobs:0 Agents:0) auxiliary(exploit/exploit_name) >> show options
Name                  Current Setting   Required  Description
----                  ---------------   --------  -----------
DBGTRACE              false             yes       Show extra debug trace info
RHOSTS                                  yes       The target host(s)
RPORT                 445               yes       The Target port (TCP)
SERVICE_DESCRIPTION                     no        Service description 
SERVICE_DISPLAY_NAME                    no        The service display name
SERVICE_NAME                            no        The service name
```
The options that are **Required** must be set by us.
```
[msf](Jobs:0 Agents:0) auxiliary(exploit/exploit_name) >> set RHOST 192.168.1.3
```
5. `run` the exploit
```
[msf](Jobs:0 Agents:0) auxiliary(exploit/exploit_name) >> run
```
# Installation
```bash
sudo apt install metasploit-framework
sudo pacman -S metasploit
```