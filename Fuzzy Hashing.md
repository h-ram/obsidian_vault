**Fuzzy hashing** is a type of hashing that allows **approximate matching** between files or data blocks. Unlike traditional cryptographic hashes (like **MD5 or SHA-256**) that change completely with small modifications, fuzzy hashes can detect **similarities** between files, even if they are slightly altered.

---
## **How Fuzzy Hashing Works**
- **Generates a hash that represents the structure of a file** rather than an exact fingerprint.
- **Compares two fuzzy hashes** to determine how similar they are.
- **Outputs a similarity score** (usually from 0 to 100), where 100 means identical files.
Example:
- If two malware variants have a **90% fuzzy hash similarity**, they are likely related.
---
## **Common Fuzzy Hashing Algorithms**
### **a) SSDeep** (Most Common)
- Uses **context-triggered piecewise hashing (CTPH)**.
- Generates **variable-length hashes** that capture patterns in the file.
- Example command to hash a file:
    ```sh
    ssdeep -b sample.exe
    ```
- Example output:
    ```
    12288:abcd1234efgh5678:ijklmnopqrstuv
    ```
### **b) TLSH (Trend Micro Locality-Sensitive Hashing)**
- Faster than SSDeep, good for large datasets.
- Generates **fixed-length** hashes.
- Example command:
    ```sh
    tlsh -c file1 file2
    ```
### **c) SDHash (Similarity Digest Hashing)**
- Focuses on detecting **similar binary data**.
- Used for **forensics and malware analysis**.
---
### **Example: Comparing Two Files with SSDeep**
1. Generate fuzzy hashes for two files:
    ```sh
    ssdeep -b file1.bin  
    ssdeep -b file2.bin  
    ```
2. Compare similarity:
    ```sh
    ssdeep -m file1.bin file2.bin  
    ```
3. Output:
    ```
    file1.bin matches file2.bin (Similarity: 85%)
    ```
---