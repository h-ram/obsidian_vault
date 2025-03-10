`setgid` (Set Group ID) is a special permission bit in Unix/Linux that allows an **executable file** to run with the **group permissions of the file’s group owner**, rather than the user’s group.
This is useful for **collaborative work** where multiple users need access to files and programs with shared group permissions.
```sh
$ ls -l filename
-rwxr-sr-x 1 root staff 12345 Jan 1 12:00 filename 
```
- The **`s` in `rwxr-sr-x`** replaces the execute (`x`) bit in the group’s permissions.
- This means that **when a user runs this file, it runs as the group owner (`staff`)**.
---
# **How to Set the `setgid` Bit**
```sh
# enable setgid
$ chmod g+s filename

# remove setgid
$ chmod g-s filename
```
---
# **Finding  `setgid` Binaries**
To list all `setgid` files:
```sh
$ find / -perm -2000 2>/dev/null
/usr/bin/crontab
/usr/bin/dotlockfile
/usr/bin/expiry
/usr/bin/ssh-agent
...Snip...
```
To check for **writable `setgid` files**:
```sh
$ find / -perm -2000 -group root -writable 2>/dev/null
```

> [!warning] Warning
> If a writable `setgid` binary exists, it is a security risk!

Common `setgid` programs:
```sh
ls -l /usr/bin/chage /usr/bin/write
-rwxr-sr-x 1 root shadow 12345 /usr/bin/chage
-rwxr-sr-x 1 root tty 12345 /usr/bin/write
```
- **`/usr/bin/chage`**: Runs with the **`shadow`** group, allowing users to modify their password expiration settings.
- **`/usr/bin/write`**: Runs with the **`tty`** group to send messages to other users' terminals.
---
# **Understanding s VS S**
```bash
$ ls -l 
-rw-r-Sr-- 1 r_macaw r_macaw 0 Feb 20 06:22 file1.sh
-rw-r-sr-- 1 r_macaw r_macaw 0 Feb 20 06:22 file2.sh
```
The uppercase **`S`** in **file1** indicates that the **setgid (s) bit is set, but the execute (x) bit is missing**.
1. **Lowercase `s`** (`-rw-r-sr--`):
    - This means **setgid is set AND the file is executable**.
    - The **execute (`x`) bit is present**.
2. **Uppercase `S`** (`-rw-r-Sr--`):
    - This means **setgid is set, BUT the file is NOT executable**.
    - The **execute (`x`) bit is missing**, so the `s` appears as **uppercase `S`**.

To make it work properly, you need to **add execute permissions**:
```sh
$ chmod g+x file1.sh
$ ls -l file1.sh
-rw-r-sr-- 1 r_macaw r_macaw 0 Feb 20 06:22 file1.sh
```
---
Related: [[setuid]]