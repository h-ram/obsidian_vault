#command 

The `file` command is used to **determine the type of a file** in Linux and Unix-like systems. It inspects a file’s **contents** instead of just relying on the file extension.

```bash
file [options] <filename>
```

```bash
# Example
$ file document.pdf

document.pdf: PDF document, version 1.7
```

---
# **Usage**

```bash
# Checking file type
file myscript.sh       # Output: myscript.sh: ASCII text

# Checking a Directory
file /home/user/       # Output: /home/user/: directory

# Checking a Symbolic Link
file mylink            # Output: mylink: symbolic link to /etc/passwd
```
---
# **Options**

```bash
# Show MIME Type
$ file -i example.jpg
example.jpg: image/jpeg; charset=binary

# Check Multiple Files
$ file file1.txt file2.txt
file1.txt: ASCII text
file2.txt: ASCII text 
```

---
# **How Does `file` Work?**
The `file` command analyzes files using three tests:
2. **Magic Number Test** – Checks the first few bytes of the file to identify its format (e.g., ELF for executables, PNG for images).
3. **Filesystem Test** – Checks if it's a directory, symbolic link, or special file.
4. **Text Encoding Test** – If it's a text file, it checks the encoding (ASCII, UTF-8, etc.).
