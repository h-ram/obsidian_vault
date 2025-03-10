#gnu_coreutils 

**GNU Core Utilities (coreutils)** is a collection of basic system commands essential for managing files, directories, and processes in Linux and Unix-like operating systems. These utilities form the foundation of command-line operations.

---
# **Installing Coreutils**
Most Linux distributions **already include** coreutils. However, if missing:
```bash
sudo apt install coreutils -y    # Debian/Ubuntu
sudo yum install coreutils -y    # CentOS/RHEL
sudo dnf install coreutils -y    # Fedora
sudo pacman -S coreutils         # Arch
brew install coreutils           # macOS (via Homebrew)
```
# **What’s Included in Coreutils?**
Some tools included in coreutils: (not all)
1. **File and Directory Management**
    - `ls` → List files and directories
    - `cp` → Copy files and directories
    - `mv` → Move or rename files
    - `rm` → Remove files or directories
    - `mkdir` → Create directories
    - `rmdir` → Remove empty directories
    - `touch` → Create empty files or update timestamps
2. **Text Processing**
    - `cat` → Concatenate and display file contents
    - `cut` → Extract specific columns of text
    - `sort` → Sort lines of text
    - `uniq` → Remove duplicate lines
    - `wc` → Count words, lines, and characters
    - `tr` → Translate or delete characters
3. **Disk and System Monitoring**
    - `df` → Display free disk space
    - `du` → Show disk usage of files and directories
    - `free` → Show memory usage
    - `uptime` → Display system uptime
    - `who` → Show logged-in users
---
