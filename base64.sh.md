#command #gnu_coreutils 

`base64` is a [[GNU Core Utilities (coreutils)|coreutils]] command used to **encode** and **decode** data in [[Base64]].
```bash
base64 [options] [FILE]
```
- `[FILE]` can be a string of text, and if ommited, it will read from standard input (stdin)
---
# **Usage**

```sh
# Encode
$ echo "Hello, World!" | base64
SGVsbG8sIFdvcmxkIQ==

$ base64 myfile.txt > encoded.txt
```

```sh
# Decode
echo "SGVsbG8sIFdvcmxkIQ==" | base64 --decode
Hello, World!

$ base64 --decode encoded.txt > original.txt
```

# **Options**

| **Option**                 | **Description**                                                           | **Example**                                |
| -------------------------- | ------------------------------------------------------------------------- | ------------------------------------------ |
| `-d`, `--decode`           | Decodes Base64-encoded data back to its original form                     | `base64 -d encoded.txt`                    |
| `-w N`, `--wrap=N`         | Wraps output lines after `N` characters (default: 76, use `0` to disable) | `base64 -w 0 file.txt`                     |
| `-i FILE`, `--input=FILE`  | Reads input from a file instead of standard input                         | `base64 -i myfile.txt`                     |
| `-o FILE`, `--output=FILE` | Writes the output to a specified file                                     | `base64 file.txt -o encoded.txt`           |

