#command 

`scp` (Secure Copy Protocol) is a **command-line tool** used to securely transfer files **between local and remote systems** over SSH.

---
## **1. Basic Syntax**
```bash
scp [options] <source> <destination>
```
- `<source>`: Path of the file to be copied.
- `<destination>`: Path where the file should be copied.
- Works with **local-to-remote**, **remote-to-local**, and **remote-to-remote** file transfers.
---
## **2. Common `scp` Commands**
### **Copy a File from Local to Remote**
```bash
scp file.txt user@remote_host:/home/user/
```
- Transfers `file.txt` from **local machine** to `/home/user/` on the **remote server**.
### **Copy a File from Remote to Local**
```bash
scp user@remote_host:/home/user/file.txt /local/directory/
```
- Downloads `file.txt` from the **remote server** to a **local directory**.
### **Copy a Directory Recursively**
```bash
scp -r my_folder user@remote_host:/home/user/
```
- Copies the entire `my_folder` from **local machine** to **remote server**.
### **Copy Using a Specific SSH Port**
```bash
scp -P 2222 file.txt user@remote_host:/home/user/
```
- Transfers `file.txt` using **port 2222** instead of the default **port 22**.
### **Use an SSH Key for Authentication**
```bash
scp -i ~/.ssh/id_rsa file.txt user@remote_host:/home/user/
```
- Uses an SSH key (`id_rsa`) instead of a password.
### **Limit Bandwidth Usage**
```bash
scp -l 100 file.txt user@remote_host:/home/user/
```
- Limits bandwidth to **100 Kbps**.
### **Enable Compression for Faster Transfers**
```bash
scp -C file.txt user@remote_host:/home/user/
```
- Compresses data during transfer.
---
## **3. Common `scp` Options**
```bash
-r   # Copy directories recursively
-P   # Specify SSH port
-i   # Use a specific SSH key
-C   # Enable compression
-l   # Limit bandwidth usage (in Kbps)
-q   # Quiet mode (suppress messages)
-v   # Verbose mode (debugging)
```
---
## **4. Differences Between `scp` and `rsync`**
- **`scp`**: Simple and secure, but copies **entire files** each time.
- **`rsync`**: More efficient for large files, as it only transfers **changed parts**.

---