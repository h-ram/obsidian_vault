#command #gnu_coreutils 

a [[GNU Core Utilities (coreutils)|coreutils]] command used to **search for files and directories in real-time** based on different criteria like **name, size, type, modification date, and permissions.

```bash
find [path] [options] [expression]
```
- **`path`** – The directory to search in (e.g., `/home/user/`).
- **`options`** – Filters like file type, size, or modification time.
- **`expression`** – Actions like printing, deleting, or executing commands on found files.
---
# **Options**
## 1. **File Type Options**
- `-type f` → Regular files
- `-type d` → Directories
- `-type l` → Symbolic links
- `-type c` → Character devices
- `-type b` → Block devices
- `-type p` → Named pipes (FIFO)
- `-type s` → Sockets
```bash
# Example: Finds all directories under `/var`.
find /var -type d
```
---
## 2. **File Name and Path Matching**
- `-name "pattern"` → Case-sensitive file name match
- `-iname "pattern"` → Case-insensitive file name match
- `-path "pattern"` → Match full path
- `-ipath "pattern"` → Case-insensitive full path match
- `-regex "pattern"` → Match using regex
- `-iregex "pattern"` → Case-insensitive regex match
```bash
find /etc -iname "*.conf"
```
Finds all `.conf` files under `/etc`, ignoring case.

---
## 3. **Size-Based Search**
- `-size +100M` → Files larger than 100MB
- `-size -50k` → Files smaller than 50KB
- `-size 1033c` → Files exactly 1033 bytes (`c` stands for bytes)
- `-size +1G` → Files larger than 1GB
```bash
find / -size +1G
```
Finds all files larger than 1GB.

---
## 4. **Permission and Ownership**
- `-perm 644` → Files with **exactly** `644` permissions
- `-perm -u=r` → Files where the owner has **read** permission
- `-perm -g=w` → Files where the group has **write** permission
- `-perm -o=x` → Files where others have **execute** permission
- `-user username` → Files owned by a specific user
- `-group groupname` → Files belonging to a specific group
```bash
find /var -perm 777
```
Finds files with **full permissions (rwx for all)**.

---
## 5. **Time-Based Search**
- `-atime +10` → Files accessed more than **10 days ago**
- `-atime -5` → Files accessed within the last **5 days**
- `-mtime +30` → Files modified more than **30 days ago**
- `-mtime -7` → Files modified within the last **7 days**
- `-ctime +20` → Files changed (metadata update) more than **20 days ago**
- `-ctime -3` → Files changed within the last **3 days**

```bash
find /home -mtime -7 -type f
```
Finds files modified within the last 7 days.

---
## 6. **File Content and Properties**
- `-empty` → Find empty files or directories
- `-readable` → Find readable files
- `-writable` → Find writable files
- `-executable` → Find executable files
```bash
find /tmp -empty
```
Finds empty files and directories in `/tmp`.

---
## 7. **Logical Operators**
- `-not` or `!` → Negate a condition
- `-o` → OR condition
- `-a` → AND condition
```bash
find /etc -type f ! -name "*.conf"
```

Finds all files **except** `.conf` files.

---
## 8. **Executing Commands on Found Files**
- `-exec command {} \;` → Run a command on each found file
- `-exec command {} +` → More efficient version
- `-ok command {} \;` → Ask for confirmation before executing
```bash
find /var/log -name "*.log" -exec rm {} \;
```
Deletes all `.log` files inside `/var/log`.
For interactive deletion:
```bash
find /var/log -name "*.log" -ok rm {} \;
```
Asks for confirmation before deleting each file.

---
## 9. **Displaying and Formatting Results**
- `-print` → Display file paths (default behavior)
- `-ls` → List details (like `ls -l`)
- `-printf "%p %s\n"` → Custom output format (path and size)
```bash
find /home -type f -printf "%p %s bytes\n"
```
Displays file paths and their sizes.

---
## 10. **Depth Control**
- `-maxdepth N` → Limit search depth to `N` levels
- `-mindepth N` → Skip first `N` levels

```bash
find /home -maxdepth 2 -type f
```
Searches for files only **up to 2 levels deep**.

---
## 11. **Deleting Files**
- `-delete` → Delete matching files
```bash
find /tmp -type f -name "*.tmp" -delete
```
Deletes all `.tmp` files in `/tmp`.

---
## 13. **Finding Symbolic Links**
- `-type l` → Find symbolic links
- `-lname "pattern"` → Find symbolic links pointing to a specific target
```bash
find / -type l -lname "/home/*"
```
Finds symlinks pointing to `/home/*`.

---
## 14. **Finding Specific File Extensions**
```bash
find /path -type f \( -name "*.txt" -o -name "*.log" \)
```
Finds all `.txt` and `.log` files.

---
## 15. **Find Files by Number of Hard Links**
- `-links n` → Find files with exactly `n` hard links
- `-links +n` → Find files with more than `n` hard links
- `-links -n` → Find files with fewer than `n` hard links
```bash
find / -type f -links +1
```
Finds files with **more than one hard link**.

---