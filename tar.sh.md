#command 

The `tar` (**Tape Archive**) command is used for creating, extracting, and managing [[Archive File|Arhcive Files]] in Linux. it is primarily used to bundle multiple files into a single archive, often compressed with `gzip`, `bzip2`, or `xz`.

```bash
tar [OPTIONS] [ARCHIVE_FILE] [FILES...]
```

```bash
# Example
tar -cvf archive.tar file1 file2 dir/
```
Creates an archive named `archive.tar` containing `file1`, `file2`, and `dir/`.

---
# **Options**
### **Basic Operations**

|Option|Description|
|---|---|
|`-c`|Create a new archive|
|`-x`|Extract (unpack) an archive|
|`-t`|List contents of an archive|
|`-f FILE`|Specify the archive filename|
|`-v`|Verbose output (show processed files)|
### **Compression Options**

|Option|Compression Type|
|---|---|
|`-z`|Compress with `gzip` (`.tar.gz` or `.tgz`)|
|`-j`|Compress with `bzip2` (`.tar.bz2`)|
|`-J`|Compress with `xz` (`.tar.xz`)|
|`--zstd`|Compress with `zstd` (`.tar.zst`)|
### **Additional Options**

|Option|Description|
|---|---|
|`-C DIR`|Extract files into `DIR`|
|`-p`|Preserve file permissions|
|`--exclude=PATTERN`|Exclude files matching `PATTERN`|
|`-r`|Append files to an existing archive|
|`-u`|Update files in an archive if they are newer|
|`--remove-files`|Remove original files after archiving|

---
# **Usage**
## **Creating Archives**

```bash
# Create an uncompressed `.tar` archive
tar -cvf archive.tar file1 file2 dir/

# Create a compressed `.tar.gz` archive
tar -czvf archive.tar.gz file1 file2 dir/  
# Same as `.tgz`:
tar -cvzf archive.tgz file1 file2 dir/

# Create a `.tar.bz2` archive
tar -cjvf archive.tar.bz2 file1 file2 dir/

# Create a `.tar.xz` archive
tar -cJvf archive.tar.xz file1 file2 dir/
```
## **Extracting Archives**

```bash
# Extract a `.tar` archive
tar -xvf archive.tar

# Extract a `.tar.gz` archive
tar -xzvf archive.tar.gz

# Extract a `.tar.bz2` archive
tar -xjvf archive.tar.bz2

# Extract a `.tar.xz` archive
tar -xJvf archive.tar.xz

# Extract files to a specific directory
tar -xvf archive.tar -C /path/to/directory/

# Extracting a Single File from an Archive
tar -xvf archive.tar file1.txt
```

## **Listing Archive Contents**

```bash
# List files in a `.tar` archive
tar -tvf archive.tar

# List contents of a `.tar.gz` archive
tar -tzvf archive.tar.gz
```
## **Adding Files to an Existing Archive**

```bash
tar -rvf archive.tar newfile.txt
```
(Note: You **cannot** add files to a compressed archive like `.tar.gz`.)
## **Removing Files After Archiving**

```bash
tar -cvf archive.tar --remove-files file1 file2
```
This deletes `file1` and `file2` after adding them to `archive.tar`.

## **Excluding Files**

```bash
# Exclude a specific file
tar -cvf archive.tar --exclude=file.txt dir/

# Exclude multiple files or patterns
tar -cvf archive.tar --exclude="*.log" --exclude="tmp/*" dir/
```
---
## **Checking Archive Integrity**
```bash
tar -tvf archive.tar > /dev/null
```
If the archive is corrupted, an error will be displayed.

---
# **Installing**
```bash
sudo pacman -S tar
sudo apt install tar
sudo dnf install tar       # Fedora, CentOS 8+, RHEL 8+
sudo yum install tar       # CentOS 7, RHEL 7
sudo zypper install tar    # OpenSUSE
sudo apk add tar           # Alpine Linux
sudo emerge sys-apps/tar   # Gentoo
sudo xbps-install -S tar   # Void Linux
```
If your distro does not have `tar` or you need a newer version, compile it from source:
```bash
wget http://ftp.gnu.org/gnu/tar/tar-latest.tar.gz
tar -xvzf tar-latest.tar.gz
cd tar-*
./configure
make
sudo make install
```
---
