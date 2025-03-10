Base64 is a binary-to-text encoding scheme that converts binary data into an ASCII string format. It is commonly used to safely transmit data over text-based protocols such as HTTP, email (MIME), and URLs, where raw binary data could cause issues.
- [[#Base64 Encoding]]
- [[#Base64 Decoding]]
- [[#Base64 Alphabet]]
- [[#Limitations of Base64]]
---
### **Base64 Encoding**
1. **Binary to 6-bit Chunks**:
    - Data is split into groups of **three bytes** (24 bits).
    - Each **24-bit chunk** is divided into **four 6-bit groups**. (pad with zeroes if not enough.)
2. **Mapping to Base64 Characters**:
    - Each 6-bit value is mapped to a character in the **[[#Base64 Alphabet]]**.
3. **Padding (`=` Character)**:
    - If the input is not a multiple of 3 bytes, `=` is added to make it a multiple of 3.
---
### **Base64 Alphabet**
Base64 encodes data using **64 characters** plus `=` for padding:
```
0-25  -> A-Z
26-51 -> a-z
52-61 -> 0-9
62    -> +
63    -> /
Padding -> =
```
---
#### **Example: Encoding "Hell"**
1. Convert to binary:
    ```
    H        e        l        l
    72       101      108      108
	01001000 01100101 01101100 01101100
    ```
2. Split into 6-bit chunks:
	```
    010010 000110 010101 101100 011011 00
    # padding with zeros
    010010 000110 010101 101100 011011 000000
    ```
3. Convert to Base64:
    ```
    18 -> S
    6  -> G
    21 -> V
    44 -> s
    27 -> b
    0  -> A
    ```
4. **Padding**: "Hell" is 4 bytes (not a multiple of 3), so two  `=` are added.
```
Hell -> SGVsbA==
```
---
### **Base64 Decoding**
- Reverse the Encoding Procsess
1. **Remove padding (`=`) if present**
2. **Convert Base64 characters to their 6-bit binary values**
3. **Reassemble the 6-bit chunks into 8-bit bytes** and remove the paddes zeros.
4. **Convert the 8-bit bytes back into the original ASCII text**

```
1.  SGVsbA== -> SGVsbA
    
2.  S -> 18 -> 010010
    G -> 6  -> 000110
    V -> 21 -> 010101
    s -> 44 -> 101100
    b -> 27 -> 011011
    A -> 0  -> 000000

3.  010010 000110 010101 101100 011011 000000
    01001000 01100101 01101100 01101100 0000

4.	01001000 -> 72  -> H
	01100101 -> 101 -> e
	01101100 -> 108 -> l
	01101100 -> 108 -> l
```
---
### **Limitations of Base64**
- **Increases Size**: Base64 encoding increases data size by **~33%** (because 3 bytes become 4 characters).
- **Not Encryption**: Base64 is an encoding scheme, **not** an encryption method (it does not provide security).
- **Not Space-Efficient**: Suitable for text-based protocols but inefficient for storage.
---