
PuTTY is a **Windows-based** application used to connect to remote systems via **SSH, SCP, FTP, ..etc**. It is also available on Linux and macOS but is mainly popular on Windows due to the lack of a built-in SSH client in older versions.

---
# **How to Use PuTTY**
1. Open **PuTTY**.
2. Enter the **Host Name (or IP address)** of the server.
3. Set **Port** to `22` (default SSH port).
4. Choose **Connection Type** → `SSH`.
5. Click **Open** → Log in with your username and password.
# **PuTTY Tools & Utilities**

|Tool|Description|
|---|---|
|**PuTTY**|SSH/Telnet client for remote access.|
|**PuTTYgen**|Generates SSH key pairs (`.ppk` files).|
|**pscp**|SCP client for secure file transfers.|
|**psftp**|SFTP client for file management.|
|**Pageant**|SSH key manager (stores private keys for authentication).|

---

# **PuTTY vs. Other SSH Clients**

|Feature|PuTTY|OpenSSH (Linux)|MobaXterm|Termius|
|---|---|---|---|---|
|SSH Support|✅|✅|✅|✅|
|SCP/SFTP|✅ (`pscp`, `psftp`)|✅|✅|✅|
|GUI Interface|✅|❌ (CLI only)|✅|✅|
|Serial Support|✅|❌|✅|✅|
|Tabbed Sessions|❌|❌|✅|✅|
|Windows Support|✅|✅|✅|✅|

# **Common PuTTY Errors & Fixes**

| Error                                             | Cause                        | Solution                            |
| ------------------------------------------------- | ---------------------------- | ----------------------------------- |
| **Connection Timed Out**                          | Firewall blocking SSH        | Check network & firewall rules.     |
| **Network Error: Connection Refused**             | SSH not enabled on server    | Ensure `sshd` is running.           |
| **Server Unexpectedly Closed Network Connection** | Incorrect key authentication | Use the correct private key format. |
| **No Supported Authentication Methods Available** | Missing username/password    | Use correct credentials.            |

---