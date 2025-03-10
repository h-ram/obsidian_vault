When people talk about "**getting a shell**" on a system, it means they have gained **command-line access** to that system, allowing them to run commands as if they were directly logged in. This is often done by exploiting **vulnerabilities** in web applications, network services, or using stolen credentials.
There are **three main types of shell connections**, each working differently:
1. [[Reverse Shell]] when the **target system** (victim) initiates a connection **back** to the attacker's system.
2. [[Bind Shell]] when the **target system opens a port** and waits for the attacker to connect to it.
3. [[Web Shell]] Runs operating system commands via the web browser using a small script (often in PHP, ASP, or Python) uploaded to a vulnerable web server.
---

|Shell Type|How It Works|Pros|Cons|
|---|---|---|---|
|**Reverse Shell**|Victim connects back to attacker|Bypasses firewalls, easy to use|Needs attacker to set up a listener|
|**Bind Shell**|Victim opens a port and waits|Simple setup, attacker connects anytime|Blocked by firewalls often|
|**Web Shell**|Web-based command execution|Easy to upload, useful for quick access|Not fully interactive, may be detected easily|
