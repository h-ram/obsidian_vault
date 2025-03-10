MD5 is a cryptographic **hash function** developed by Ronald Rivest in **1991**. It takes an input of any length and produces a **128-bit (16-byte) hash value**, typically represented as a **32-character hexadecimal string**.
### **How MD5 Works**
1. **Input Processing** – The data is divided into 512-bit chunks.
2. **Padding** – Extra bits are added so that the message length is a multiple of 512 bits.
3. **Processing in Rounds** – The algorithm applies bitwise operations, modular addition, and logical functions in **64 rounds**.
4. **Final Hash Output** – The result is a **128-bit hash** (e.g., `"5d41402abc4b2a76b9719d911017c592"` for `"hello"`).
### **Weaknesses of MD5**
MD5 was once widely used for **password hashing, checksums, and digital signatures**, but it is now considered **insecure** due to:
1. **Collisions** – Two different inputs can produce the same hash.
2. **Fast Computation** – Attackers can brute-force hashes quickly.
3. **Rainbow Table Attacks** – Precomputed hash tables make cracking passwords easier.