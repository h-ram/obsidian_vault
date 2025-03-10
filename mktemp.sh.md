#command #gnu_coreutils 

**`mktemp`** is a [[GNU Core Utilities (coreutils)|coreutils]] command used to create **temporary files and directories** . It ensures unique filenames to **prevent conflicts**.
```bash
mktemp [OPTIONS] [TEMPLATE]
```
- If **no template** is provided, `mktemp` generates a random filename in `/tmp/`.
- If a **template** is provided, `mktemp` replaces the last six `X`s in the template with random characters.
---
# **Options**
| Option         | Description                                           |
| -------------- | ----------------------------------------------------- |
| `-d`           | Create a **temporary directory** instead of a file.   |
| `-p DIR`       | Specify a **custom directory** for the temp file.     |
| `-u`           | Generate a name but **don’t create a file** (unsafe). |
| `--suffix=SFX` | Append a **suffix** to the filename.                  |

---
# **Usage**

```bash
# Creating Temporary Files
$ mktemp
/tmp/tmp.zxJ3Kd
```
- This creates a **unique temporary file** in `/tmp/`.
- The file is **empty** and **only accessible by the user** who created it (`rw-------` permissions).

```bash
# Using a Custom Template
mktemp mytempfileXXXXXX
mytempfileA1B2C3
```
- The last **six `X`s are replaced** with random characters. (they're mandatory)
- If fewer than six `X`s are provided, an error occurs.
---
```bash
# Creating Temporary Directories (-d)
mktemp -d
/tmp/tmp.4pLk9s
```
- This creates a **temporary directory** instead of a file.
- Useful for creating **isolated workspaces**.

---
By default, temporary files go into `/tmp/`. To change this:
```bash
# Specifying a Custom Directory (`-p DIR`)**
mktemp -p /home/user mytempXXXXXX
/home/user/mytempHidk69
```
- This creates a temporary file in `/home/user/`.
---

```bash
# Creating a Temp File for a Script
tempfile=$(mktemp)
echo "Processing..." > "$tempfile"
cat "$tempfile"
rm "$tempfile"  # Clean up after use
```
---
```bash
## **Creating a temporary directory and changing to it.j **
cd "$(mktemp -d)"
```
---