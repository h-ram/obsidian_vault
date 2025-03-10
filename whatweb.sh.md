#command 
A tool used for **web application fingerprinting**. It scans websites to identify the technologies, software, and services they are running. It can detect things like web servers, CMS (Content Management Systems), programming languages, frameworks, and much more.

---
# Usage

#### **Basic Usage:**
- To scan a website and identify its technologies:
    ```bash
    whatweb http://example.com
    ```
#### **Scan with More Details:**
- To get more detailed output about the technologies detected, use the `-v` (verbose) flag:
    ```bash
    whatweb -v http://example.com
    ```
#### **Scan Multiple Websites:**
- You can scan a list of websites from a file:
    ```bash
    whatweb -i sites.txt
    ```
    Where `sites.txt` contains a list of URLs (one per line).
#### **Show Specific Information:**
- To filter the output and show only specific information, use `-t` (type):
    ```bash
    whatweb -t 3 http://example.com
    ```
   The `-t` flag adjusts the level of detail shown in the output (1 for basic, 2 for more detailed, 3 for full fingerprinting).
#### **Use Stealth Mode:**
- To minimize detection while running WhatWeb, you can use the `--quiet` option to avoid verbose output:
    ```bash
    whatweb --quiet http://example.com
    ```
#### **Save the Output:**
- To save the output to a file for further analysis:
    ```bash
    whatweb http://example.com > output.txt
    ```
### **Output Example**
```bash
WhatWeb 0.5.1 (https://github.com/urbanadventurer/WhatWeb)

http://example.com
  Server    Apache/2.4.7 (Ubuntu)
  CMS       WordPress 5.7
  Javascript jQuery 3.6.0
  SSL       SSLv3, TLSv1, TLSv1.2
  HTTP Headers X-Powered-By: PHP/7.4.3
```
---
# Installation
```
sudo apt install whatweb
yay -S whatweb
```
