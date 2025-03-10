#networking 

A  **hostname** is the **unique name of a device** on a network used to identify it.
```bash
#Linux/Mac
hostname

#Windows
hostname
echo %COMPUTERNAME%
```
* **Case-insensitive**: hostnames `Server1` and `server1` are treated as the same.
* **Max Length:** up to 253 characters
* **Allowed Characters:**
	* **Letters:** `A-Z`, `a-z`
	* **Numbers:** `0-9`  
	* **Hyphens (`-`)** (but cannot start or end with one)
	* ❌ No underscores ( `_` ) Allowed
---
### **Examples of Hostnames**
- **Local Network Hostnames:**
    - `my-laptop` (your personal computer)
    - `server1` (a company's internal server)
    - `printer-office` (a networked printer)
- **Internet Hostnames (Part of a Domain Name):**
    - `www.google.com` (`www` is the hostname)
    - `mail.yahoo.com` (`mail` is the hostname)
    - `ftp.example.com` (`ftp` is the hostname for an FTP server)
---
# Changing Hostname
#### Linux/Mac
```bash
# temporarly change
sudo hostname new-hostname

# Permanent change
sudo hostnamectl set-hostname new-hostname
```
#### Windows
- Open **Control Panel → System → Advanced System Settings**.
- Click **Computer Name → Change**.
- Enter a new hostname and restart your PC.
---
