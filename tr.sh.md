#command #gnu_coreutils 

`tr` (translate) is a [[GNU Core Utilities (coreutils)|coretutils]]command used for **text transformation**, such as **character replacement, deletion, and compression** of repeated characters. It processes input from **stdin** and outputs the transformed text to **stdout**.
```sh
tr [OPTION] SET1 [SET2]
```
- **`SET1`**: Characters to replace.
- **`SET2`**: Characters to replace with (used for translation).
- If `SET2` is omitted, `tr` performs **deletion** or **compression** instead of translation.
---
# **Usage**
### **1. Translating Characters**
Replace characters from `SET1` with corresponding ones from `SET2`.
```sh
$ echo "hello world" | tr 'a-z' 'A-Z'
HELLO WORLD

$ echo "Hello World" | tr ' ' '_'
Hello_World
```
---
### **2. Deleting Characters (`-d`)**
Removes all occurrences of characters in `SET1`.
```sh
$ echo "hello world" | tr -d 'aeiou'
hll wrld

$ echo "a1b2c3d4" | tr -d '0-9'
abcd
```
---
### **3. Squeezing Repeated Characters (`-s`)**
Replaces **consecutive** occurrences of a character with a single one.
```sh
$ echo "Hello    World" | tr -s ' '
Hello World

$ cat file.txt | tr -s '\n'
# (All consecutive newlines are reduced to one)
```
---
### **4. Complement (`-c`): Inverting Character Sets**
`-c` means **"take everything except SET1"**.
```sh
$ echo "a1b2c3d4" | tr -cd '0-9'
1234
```
---
# **Options**

|**Option**|**Description**|**Example**|
|---|---|---|
|`-d`|Delete characters in `SET1`|`tr -d '0-9'` (removes digits)|
|`-s`|Squeeze multiple occurrences into one|`tr -s ' '` (reduces spaces)|
|`-c`|Complement (`SET1` becomes everything except its characters)|`tr -cd '0-9'` (keeps only digits)|

---