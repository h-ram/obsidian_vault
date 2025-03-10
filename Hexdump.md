A **hexdump** is a hexadecimal representation of binary data. It displays the raw content of a file or memory in a structured format, typically showing:
1. **Offset (Address)** – The position of bytes in the file or memory.
2. **Hexadecimal Data** – The actual bytes in hex format.
3. **ASCII Representation** – A readable translation of the bytes, if printable.

```bash
$ hexdump -C file.bin
00000000  48 65 6c 6c 6f 2c 20 57  6f 72 6c 64 21 0a    |Hello, World!.|
```

It is called a **hexdump** because it "dumps" (displays) the contents of a file or memory in **hexadecimal (hex) format**.