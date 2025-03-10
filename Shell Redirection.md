
Redirection in Linux allows you to control the input and output of commands. You can redirect **standard input (stdin)**, **standard output (stdout)**, and **standard error (stderr)** to files, other commands, or devices like `/dev/null`.

---
# **Standard Streams**
Linux provides three standard data streams:

|Stream|Number|Description|
|---|---|---|
|**stdin**|`0`|Standard Input (keyboard input)|
|**stdout**|`1`|Standard Output (normal command output)|
|**stderr**|`2`|Standard Error (error messages)|
By default, `stdout` and `stderr` print to the terminal, while `stdin` reads from the keyboard.

---
# **Redirecting Output (stdout)**
- `>` → Redirects output to a file, **overwriting** it.
- `>>` → Redirects output to a file, **appending** to it.
```bash
# Examples
echo "Hello, World!" > output.txt  # Overwrites output.txt
echo "New line" >> output.txt      # Appends to output.txt
```
---
# **Redirecting Errors (stderr)**
- `2>` → Redirects **stderr** to a file.
- `2>>` → Appends stderr to a file.
```bash
# Example
ls non_existent_file 2> error.log  # Save error message to error.log
ls another_missing_file 2>> error.log  # Append error to error.log
```
 **Suppress Errors (`2>/dev/null`)**
```bash
command 2>/dev/null
```
This sends error messages to `/dev/null`, which discards them.

---
# **Redirecting stdout and stderr Together**
### **Method 1: `2>&1`**
- `2>&1` → Redirects **stderr** to stdout.
- `>` redirects stdout to a file.
```bash
# Example
ls file1 file2 > output.log 2>&1  # Save both stdout & stderr in output.log
```
**Breakdown:**
1. `> output.log` → Redirect stdout to `output.log`
2. `2>&1` → Redirect stderr to **the same place as stdout** (`output.log`)
### **Method 2: `&>` (Shortcut)**
- `&>` redirects both stdout and stderr.
```bash
# Example
command &> output.log
```
---
# **Redirecting Input (stdin)**
### **Using `<` to Read Input from a File**
```bash
command < input.txt
```
Example:
```bash
wc -l < file.txt  # Count lines in file.txt
```
---
# **Combining Multiple Redirections**
You can mix stdin, stdout, and stderr redirections.
```bash
# Example
command < input.txt > output.txt 2> error.log
```
- Reads input from `input.txt`
- Writes output to `output.txt`
- Writes errors to `error.log`
---
# **Here Documents (`<<`) and Here Strings (`<<<`)**
### **Here Document (`<<`)**
Used to provide multi-line input to a command.
```bash
cat <<EOF
Hello, this is a multi-line string.
It will be passed as input to `cat`.
EOF
```
### **Here String (`<<<`)**
Used for single-line input.
```bash
grep "word" <<< "This is a test word."
```
---
# **Final Cheat Sheet**

| Symbol        | Meaning                          |
| ------------- | -------------------------------- |
| `>`           | Redirect stdout (overwrite)      |
| `>>`          | Redirect stdout (append)         |
| `2>`          | Redirect stderr (overwrite)      |
| `2>>`         | Redirect stderr (append)         |
| `2>&1`        | Redirect stderr to stdout        |
| `&>`          | Redirect both stdout and stderr  |
| `<`           | Redirect stdin from a file       |
| `             | `                                |
| `<<`          | Here document (multi-line input) |
| `<<<`         | Here string (single-line input)  |
| `2>/dev/null` | Discard stderr                   |
