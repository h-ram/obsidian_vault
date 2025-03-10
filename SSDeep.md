**SSDeep** is a fuzzy hashing tool that uses **Context-Triggered Piecewise Hashing (CTPH)** to identify **similarities** between files, even if they are not identical. Unlike cryptographic hashes (e.g., MD5, SHA-256), which change completely with small modifications, SSDeep produces **variable-length hashes** that allow **partial matching**.

---
## **How SSDeep Works**
- **Splits a file into multiple chunks** based on content patterns.
- **Generates a hash for each chunk** using rolling hashing.
- **Outputs a final "fuzzy hash"** that represents the file structure.
- **Compares fuzzy hashes** to measure similarity (0-100%).
---
## **SSDeep Hash Example**
Example command to generate a hash for a file:
```sh
ssdeep -b sample.txt
```
Output:
```
12288:abcd1234efgh5678:ijklmnopqrstuv
```
- The **first number (12288)** is the block size.
- The **two parts after (abcd1234efgh5678, ijklmnopqrstuv)** are hashed segments.
---
## **Comparing Files Using SSDeep**
Command to compare two files:
```sh
ssdeep -m file1.bin file2.bin
```
Output:
```
file1.bin matches file2.bin (Similarity: 85%)
```
This means **file1.bin and file2.bin share 85% similarity**.

---