#command 

`xxd` is used to **create [[Hexdump|Hexdumps]]** (hexadecimal representations of binary files) and **reverses hexdumps back into binary**. Also used for [[Hex Encoding]].

```bash
xxd [options] [file]
```
Example:
```bash
$ xxd file.bin
00000000: 6865 6c6c 6f74 6865 7265 7368 6f72 7479  hellothereshorty
```
---
# **Understanding `xxd` Output**

```bash
# Example
$ echo "Hello, World!" | xxd
00000000: 4865 6c6c 6f2c 2057 6f72 6c64 210a  Hello, World!.
```

| Offset     | Hexadecimal Data                            | ASCII Equivalent |
| ---------- | ------------------------------------------- | ---------------- |
| `00000000` | `48 65 6c 6c 6f 2c 20 57 6f 72 6c 64 21 0a` | `Hello, World!`  |
- **Offset (`00000000`)** – Byte position in the file.
- **Hexadecimal (`4865 6c6c ...`)** – Encoded binary data.
- **ASCII Equivalent (`Hello, World!`)** – Human-readable text.

---
# **Options**

|Option|Description|Example|
|---|---|---|
|`-r`|Reverse operation: converts hex dump back to binary|`xxd -r file.hex > file.bin`|
|`-p`|Output in **plain hex** (no offsets, no ASCII)|`xxd -p file.bin`|
|`-c <n>`|Change **columns per line** (default: 16)|`xxd -c 8 file.bin`|
|`-g <n>`|Group bytes (`1, 2, 4, 8` allowed)|`xxd -g 2 file.bin`|
|`-s <offset>`|Skip bytes before starting dump|`xxd -s 10 file.bin`|
|`-l <length>`|Limit output to **N bytes**|`xxd -l 32 file.bin`|
|`-u`|Uppercase hex output|`xxd -u file.bin`|
|`-i`|Output as a **C array**|`xxd -i file.bin`|
|`-b`|Output in **binary (bits)** instead of hex|`xxd -b file.bin`|
|`-e`|Little-endian 32-bit hexdump|`xxd -e file.bin`|
|`-a`|Auto-skip lines with repeated data|`xxd -a file.bin`|

---
# **Usage**

```bash
# Create a Hexdump
$ echo "Hey ladies :)" | xxd 
00000000: 4865 7920 6c61 6469 6573 203a 290a     Hey ladies :).

# Display Without ASCII Column (-p)
$ echo "Hey ladies :)" | xxd -p
486579206c6164696573203a290a

# Reverse Hexdump (Convert Back to Binary)
$ xxd -r file.hex > file.bin

# Customizing Line Width (-c)
	xxd -c 8 file.bin    # Limits output to 8 bytes per line instead of 16.

# Changing Byte Grouping (-g)
xxd -g 2 file.bin    # Groups bytes into 2-byte chunks instead of 4

# Skipping Bytes (-s)
xxd -s 10 file.bin   # Starts hex dumping from byte 10.

# Limiting Output (-l)
xxd -l 32 file.bin   # Dumps only the first 32 bytes
```

---
# **Installation**
`xxd` is bundled with **Vim**, installing Vim also installs `xxd`.

```bash
sudo apt install vim-common
sudo dnf install vim-common 
sudo yum install vim-common
sudo pacman -S vim
brew install vim
```

# **Etymology**
The name **`xxd`** does not have an officially documented meaning, but a possible meaning is:
1. **"xx"** – Hex 
2. **"d"** – dump