`setuid` (Set User ID) is a special permission bit in Unix/Linux that allows an **executable file** to run with the **privileges of the file's owner**, instead of the user who executes it.
- Normally, when a user runs a program, it executes with **their own user ID**.
- If a program has the **setuid** bit set, it runs with the **user ID of the file's owner**.
This is particularly useful when a normal user needs to execute an operation that typically requires **higher privileges**.

```sh
$ ls -l filename
-rwsr-xr-x 1 james james 12345 Jan 1 12:00 filename
```
- The **`s` in `rwsr-xr-x`** replaces the execute (`x`) bit in the owner’s permissions.
- This means that whenever a user runs this file, **it executes as if the owner "james" executed it**.

---
# **How to Set the `setuid` Bit**
```sh
# enable setuid
$ chmod u+s filename

# remove setuid:
$ chmod u-s filename
```
---
# **Finding `setuid` Binaries**
To list all `setuid` files:
```sh
$ find / -perm -4000 2>/dev/null
/usr/bin/passwd
/usr/bin/pkexec
/usr/bin/su
/usr/bin/sudo
/usr/bin/umount
...Snip...
```
To check for **writable `setuid` files**:
```sh
find / -perm -4000 -user root -writable 2>/dev/null
```

> [!warning] Warning
> If a writable `setuid` binary exists, it is a security risk!

Common `setuid` programs:
```sh
ls -l /bin/su /usr/bin/passwd
-rwsr-xr-x 1 root root 12345 /bin/su
-rwsr-xr-x 1 root root 12345 /usr/bin/passwd
```
- **`/usr/bin/passwd`**: Runs as root because it needs to modify `/etc/shadow`.
- **`/bin/su`**: Allows switching users by running as root.

---
# **Understanding s VS S**
```bash
$ ls -l 
-rwSr--r-- 1 r_macaw r_macaw 0 Feb 20 06:22 file1.sh
-rwsr--r-- 1 r_macaw r_macaw 0 Feb 20 06:22 file2.sh
```
The uppercase **`S`** in **file1** indicates that the **setuid (s) bit is set, but the execute (x) bit is missing**.
1. **Lowercase `s`** (`-rwsr--r--`):
    - This means **setuid is set AND the file is executable**.
    - The **execute (`x`) bit is present**.
2. **Uppercase `S`** (`-rwSr--r--`):
    - This means **setuid is set, BUT the file is NOT executable**.
    - The **execute (`x`) bit is missing**, so the `s` appears as **uppercase `S`**.

To make it work properly, you need to **add execute permissions**:
```sh
$ chmod u+x file1.sh
$ ls -l file1.sh
-rwsr--r-- 1 r_macaw r_macaw 0 Feb 20 06:22 file1.sh
```

---
Related: [[setgid]]