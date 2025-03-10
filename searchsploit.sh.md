#command 

A Tool for searching public exploits/vulnerabilities for any applications
```bash
searchsploit [options] [search_terms]
```
---
# Usage
```bash
# Search for exploits related to a specific software
searchsploit apache

# Search for exploits related to a specific software and version
searchsploit apache 2.4.7

# Search for exploits with a specific title
searchsploit -t "remote code execution"


# Update the local Exploit Database
searchsploit --update

```
---
# Options
```bash
-h, --help: Display help information.
-v, --version: Show the version of SearchSploit.
-u, --update: Update the local Exploit Database.
-t, --title: Search only in the exploit titles.
-e, --exact: Perform an exact match search.
-s, --strict: Perform a strict search.
-j, --json: Show results in JSON format.
-m, --mirror: Copy an exploit to the current working directory.
-p, --path: Show the path to the exploit.
-c, --case: Perform a case-sensitive search.
-x, --exclude: Exclude results containing the specified term.
```
# Installation
```
sudo apt install exploitdb
sudo pacman -S exploitdb
```
