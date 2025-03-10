**SecLists** (Security Lists) is a collection of wordlists, payloads, and test cases used by security professionals for various tasks in **penetration testing** and **security assessments**. It’s maintained by **Daniel Miessler** and is hosted on GitHub.

---
### **Common Lists**
### 1. **Discovery/Web-Content**
- **common.txt**: A widely used wordlist for **directory brute-forcing** with tools like **Gobuster** or **DirBuster**. This list contains common web directories and file names (e.g., `/admin`, `/login`, `/uploads`, etc.).
    - Path: `SecLists/Discovery/Web-Content/common.txt`
- **big.txt**: A larger wordlist for directory brute-forcing, containing a wider variety of potential directory and file names.
    - Path: `SecLists/Discovery/Web-Content/big.txt`
- **raft-large-words.txt**: Another large wordlist used for brute-forcing web directories.
    - Path: `SecLists/Discovery/Web-Content/raft-large-words.txt`
### 2. **Passwords**
- **rockyou.txt**: One of the most popular and well-known password lists, containing over 14 million common passwords. It’s often used for **password cracking** or **brute-forcing** login credentials.
    - Path: `SecLists/Passwords/Leaked-Databases/rockyou.txt`
- **darkc0de.lst**: A password list with a variety of common passwords, often used in password cracking or brute-forcing attacks.
    - Path: `SecLists/Passwords/darkc0de.lst`
- **10-million-password-list-top-10000.txt**: A list containing the top 10,000 most common passwords.
    - Path: `SecLists/Passwords/10-million-password-list-top-10000.txt`

### 3. **Subdomains**
- **subdomains-top1million-5000.txt**: A wordlist used for **subdomain enumeration**, containing the most common subdomains for a given domain. It’s useful when trying to discover subdomains during reconnaissance.
    - Path: `SecLists/Subdomains/subdomains-top1million-5000.txt`
### 4. **Fuzzing**
- **fuzzing.txt**: A generic fuzzing list that includes common values used to test for vulnerabilities in inputs (e.g., SQLi, XSS).
    - Path: `SecLists/Fuzzing/fuzzing.txt`
- **bypass.txt**: Used for testing common attack vectors like **SQL injection** and **XSS**.
    - Path: `SecLists/Fuzzing/bypass.txt`
### 5. **Vulnerabilities and Payloads**
- **xss-payloads.txt**: A list of **XSS payloads** for testing and exploiting **Cross-Site Scripting** vulnerabilities.
    - Path: `SecLists/Payloads/xss-payloads.txt`
- **sql-injection-payloads.txt**: A list of **SQL injection** payloads.
    - Path: `SecLists/Payloads/sql-injection-payloads.txt`
### 6. **Miscellaneous**
- **user-agents.txt**: A list of common **user-agents**, useful for simulating different browsers or devices in web scraping, automation, or vulnerability testing.
    - Path: `SecLists/Miscellaneous/user-agents.txt`
- **common-names.txt**: A list of common names, often used for testing or finding misconfigured **DNS** records or **virtual hosts**.
    - Path: `SecLists/Miscellaneous/common-names.txt`
---
### Installation
```bash
git clone https://github.com/danielmiessler/SecLists

yay -S seclists
sudo apt install seclists
```

> [!NOTE] NOTEJ
> If SecLists is installed via a package manager it will be storred in `/usr/share/seclists/`
