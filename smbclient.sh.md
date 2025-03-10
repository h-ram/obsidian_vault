#command  
### **SMB Command in Linux (`smbclient`) – Detailed Explanation**
The `smbclient` command is a command-line tool used to interact with **SMB (Server Message Block)** shares on a network. It works similarly to an **FTP client** but is used for **Windows and Samba file shares**.

---

## **1. Basic Syntax**

```bash
smbclient [OPTIONS] //server/share -U username
```

- `//server/share` → The **SMB server and share name**.
- `-U username` → Specifies the **username** to authenticate with.

---

## **2. Connecting to an SMB Share**

To connect to an SMB share, run:

```bash
smbclient //192.168.1.100/shared_folder -U user
```

It will prompt for a **password**, then open an interactive SMB shell.

Example output:

```
Enter WORKGROUP\user's password:
smb: \> _
```

To connect anonymously (if allowed):

```bash
smbclient //192.168.1.100/shared_folder -N
```

(`-N` means **no password**)

---

## **3. Listing Available SMB Shares**

Before connecting, you can **list available shared folders** on a remote machine:

```bash
smbclient -L //192.168.1.100 -U user
```

Example output:

```
Sharename       Type      Comment
---------       ----      -------
Public          Disk      Shared public folder
Private         Disk      Private user folder
IPC$            IPC       Remote IPC
```

- `Disk` → A shared folder (file storage).
- `IPC$` → Inter-process communication (not a file share).

---

## **4. SMB Commands Inside `smbclient`**

Once inside the SMB shell, you can use various commands:

|Command|Description|
|---|---|
|`ls`|List files in the share.|
|`cd <dir>`|Change directory inside the share.|
|`pwd`|Show current directory.|
|`get <file>`|Download a file from the share.|
|`mget <file1> <file2>`|Download multiple files.|
|`put <file>`|Upload a file to the share.|
|`mput <file1> <file2>`|Upload multiple files.|
|`mkdir <dir>`|Create a directory on the share.|
|`rmdir <dir>`|Remove a directory.|
|`rm <file>`|Delete a file.|
|`exit` or `q`|Quit `smbclient`.|

**Example: Download a file**

```bash
smb: \> get myfile.txt
```

**Example: Upload a file**

```bash
smb: \> put localfile.txt
```

---

## **5. Mounting an SMB Share (Alternative to `smbclient`)**

Instead of using `smbclient`, you can **mount** the SMB share like a normal filesystem.

### **Mount an SMB Share on Linux**

```bash
sudo mount -t cifs -o username=user,password=pass //192.168.1.100/shared_folder /mnt/smb
```

To unmount:

```bash
sudo umount /mnt/smb
```

---

## **6. Using `smbclient` in Scripts**

You can automate SMB tasks using a **batch mode**:

```bash
smbclient //192.168.1.100/share -U user%password -c "ls; get file.txt; exit"
```

This will:

1. **List files**
2. **Download `file.txt`**
3. **Exit**

---

## **7. Checking SMB Protocol Version**

To check which SMB version is supported:

```bash
smbclient -L //192.168.1.100 -m SMB3 -U user
```

(`-m SMB3` forces SMBv3 protocol)

---

## **8. Common Troubleshooting**

- **Access Denied?**
    - Ensure the **username and password** are correct.
    - Try specifying the **workgroup/domain**:
        
        ```bash
        smbclient //192.168.1.100/share -U DOMAIN\\user
        ```
        
- **Can't List Shares?**
    - Check if the SMB service is running on the server.
    - Use `-m SMB2` or `-m SMB3` to force a protocol version.

---

### **Conclusion**

- `smbclient` is a powerful **SMB file transfer tool**.
- Supports **listing, downloading, uploading, and managing files**.
- Can be used interactively or **automated in scripts**.
- For permanent access, **mount SMB shares** using `mount -t cifs`.

Would you like help **configuring a Samba server** or **debugging SMB issues**?