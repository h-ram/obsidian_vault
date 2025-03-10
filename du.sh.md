#command #gnu_coreutils

`du` (**Disk Usage**) is a [[GNU Core Utilities (coreutils)|coreutils]] command used to  **estimate and display the size of files and directories**. It helps users analyze disk space usage.

```bash
du [OPTIONS] [FILE or DIRECTORY]
```
If no file or directory is specified, `du` assumes the current directory (`.`).

---
# **Usage**

```bash
# Check Disk Usage of a Directory
$ du /home/user
4000    /home/user/Documents
12000   /home/user/Downloads
16000   /home/user

# Check Disk Usage of a File
$ du myfile.txt
5000 mfile.txt
```
Each number represents the size in **kilobytes (KB)** by default.

---
# **Options**
### **1. Show Human-Readable Sizes (`-h`)**
```bash
$ du -h /home/user

3.9M    /home/user/Documents
11.7M   /home/user/Downloads
15.6M   /home/user
```
The `-h` option makes sizes easier to read (**K, M, G** for KB, MB, GB).

---
### **2. Show Only Total Directory Size (`-s`)**
```bash
$ du -sh /home/user

15.6M   /home/user
```
The `-s` option (**summary**) prevents listing every subdirectory.

---
### **3. Show Sizes of All Files and Directories (`-a`)**
```bash
du -ah /home/user

500K    /home/user/file1.txt
1.2M    /home/user/image.png
3.9M    /home/user/Documents
15.6M   /home/user
```
The `-a` option includes **files**, not just directories.

---
### **4. Limit Depth of Output (`--max-depth=N`)**
```bash
$ du -h --max-depth=1 /home/user

3.9M    Documents
11.7M   Downloads
15.6M   /home/user
```
Only **top-level** directories are shown. Replace `1` with `2` for more levels.

---
### **5. Show Disk Usage in Blocks (`-B`)**
Specify the block size manually:
```bash
$ du -B MB /home/user

4MB     Documents
12MB    Downloads
16MB    /home/user
```

---
### **6. Sort Output by Size**
```bash
du -ah /home/user | sort -rh | head -10
```
- `sort -rh` → Sorts in **reverse** (largest first).
- `head -10` → Shows **top 10 largest** files/folders.
---
### **7. Find the Largest Files**
```bash
du -ah /home/user | sort -rh | grep -v '/$' | head -5
```
This filters out directories (`grep -v '/$'`), showing only **largest files**.

---
### **8. Exclude Certain Files or Directories (`--exclude`)**
```bash
du -h --exclude='*.mp4' /home/user
```
This excludes **all `.mp4` files**.

---
# **Difference Between `du` and [[df.sh|df]]**

| Command | Purpose                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| `du`    | Shows the **size of files/directories** based on their actual storage usage. |
| `df`    | Shows the **free and used space** of an entire disk or partition.            |
```bash
# Example:
$ df -h /

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G  80G  20G   80%  /
```

---