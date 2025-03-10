#command #gnu_coreutils 

`df` (**disk free**) is a [[GNU Core Utilities (coreutils)|coreutils]] command used to **display available and used disk space** on mounted filesystems. It helps monitor storage usage on a system.

```bash
df [OPTIONS] [FILESYSTEM]
```
If no filesystem is specified, `df` shows information for **all mounted filesystems**.

---
# **Usage**
```bash
# Check Disk Space Usage
$ df

Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1      100000000  60000000  40000000  60% /
tmpfs            2000000         0   2000000   0% /dev/shm
/dev/sdb1       50000000  30000000  20000000  60% /data
```
- **Filesystem** → Device name (e.g., `/dev/sda1`).
- **1K-blocks** → Total size in 1K blocks.
- **Used** → Space already used.
- **Available** → Free space left.
- **Use%** → Percentage of space used.
- **Mounted on** → Mount point (directory where the filesystem is attached).

---
# **Options**
### **1. Show Human-Readable Sizes (`-h`)**
```bash
$ df -h

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   60G   40G  60% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
/dev/sdb1        50G   30G   20G  60% /data
```
The `-h` option converts blocks into **KB, MB, GB, TB**.

---
### **2. Show Disk Space in Specific Units**
- **Megabytes (`-BM`)**:
```bash
$ df -BM
```
- **Gigabytes (`-BG`)**:
```bash
$ df -BG
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   60G   40G  60% /
```

---
### **3. Show Only a Specific Filesystem**
```bash
$ df -h /dev/sda1
```
or
```bash
$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   60G   40G  60% /
```

---
### **4. Show Filesystem Types (`-T`)**
```bash
$ df -T
Filesystem     Type  1K-blocks    Used Available Use% Mounted on
/dev/sda1      ext4  100000000 60000000  40000000  60% /
tmpfs          tmpfs   2000000        0   2000000   0% /dev/shm
/dev/sdb1      xfs   50000000 30000000  20000000  60% /data
```
This helps identify the **type of filesystem** (e.g., `ext4`, `xfs`, `tmpfs`).

---
### **5. Show Inodes Instead of Space (`-i`)**
```bash
$ df -i
Filesystem      Inodes   IUsed    IFree IUse% Mounted on
/dev/sda1      10000000  600000  9400000    6% /
```
- **Inodes** are metadata structures that store file information.
- If inodes run out, **no new files can be created**, even if space is available.
---
### **6. Show Only Local Filesystems (`-l`)**
```bash
df -hl
```
This excludes network filesystems like NFS.

---
### **7. Exclude Specific Filesystems (`-x <fstype>`)**
Exclude `tmpfs` (temporary filesystems):
```bash
df -h -x tmpfs
```
---
### **8. Monitor Disk Usage Continuously**
To check disk usage every 2 seconds:
```bash
watch -n 2 df -h
```

---
# **Difference Between `df` and [[du.sh|du]]**

| Command | Purpose                                                               |
| ------- | --------------------------------------------------------------------- |
| `df`    | Shows **total disk space, used, and available space per filesystem**. |
| `du`    | Shows **disk usage per file and directory**.                          |
```bash
# Example
$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   60G   40G  60% /

$ du -sh /
30G     /
```
- **`df`** includes **everything** (even reserved space).
- **`du`** only shows **actual file usage**.
---