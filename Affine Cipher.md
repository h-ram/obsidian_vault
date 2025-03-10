#cryptography 

The Affine Cipher gets its name from the **[[Affine Transformation]]** in mathematics, which involves a linear function. In this cipher, each letter is transformed using a math formula.
**Encryption formula**:
$$E(x)=(a⋅x+b) \mod  m$$
- x is the numerical value of a letter.
- a is the multiplier (key), a constant chosen by us.
- b is the shift (key), a constant chosen by us.
- m is the size of the alphabet. (usually 26 for the English alphabet).
**Decryption formula**:
$$D(y)= a^{−1}⋅(y−b)\mod m$$
- y is the ciphertext letter (in numerical form).
- $a^{-1}$ is the modular inverse of a modulo m (use the extended Euclidean algorithm to find it)
- b is the shift value used in encryption.
- m is the size of the alphabet (usually 26 for the English alphabet).
# Example
### Encryption
We’ll encrypt the word **"HELLO"** using the Affine Cipher formula: $E(x)=(a⋅x+b) \mod  m$
1. **Choose the keys**:
	- a = 5 (the multiplier)
	- b = 8 (the shift)
	- m = 26 (the alphabet size)
2. **Convert the letters to numbers**:
	- H = 7, E = 4, L = 11, L = 11, O = 14
3. **Apply the formula to each letter**:
	- For H (x = 7): $E(7)=(5⋅7+8) mod  26 = 17(R)$
	- For E (x = 4): $E(4)=(5⋅4+8)mod  26 = 2(C)$
	- For L (x = 11): $E(11)=(5⋅11+8)mod  26 = 11(L)$
	- For the second L: Same calculation, result = 11 (L).
	- For O (x = 14): $E(14)=(5⋅14+8)mod  26 = 0(A)$
4. **Ciphertext**:
	- The encrypted word is **"RCLLA"**.
### Decryption
To decrypt, we reverse the process using the formula: $D(y)=a^{−1}⋅(y−b)mod  m$
Where $a^{-1}$ is the **modular multiplicative inverse** of $a$ modulo m.
1. **Find $a^{-1}$:**
    - a = 5, m = 26.
    - Solve $5 \cdot a^{-1} \equiv 1 \mod 26$.
    - $a^{-1} = 21$ (you can calculate this using the extended Euclidean algorithm).
2. **Decrypt each letter** (numbers from ciphertext "RCLLA"):
    - For R (y = 17):  $D(17) = 21 \cdot (17 - 8) \mod 26 = 7 \quad (\text{H})$
    - For C (y = 2):  $D(2) = 21 \cdot (2 - 8) \mod 26 = 4 \quad (\text{E})$
    - For L (y = 11):  $D(11) = 21 \cdot (11 - 8) \mod 26 = 11 \quad (\text{L})$
    - Repeat for the second (L).
    - For A (y = 0):  $D(0) = 21 \cdot (0 - 8) \mod 26 = 14 \quad (\text{O})$
3. **Plaintext**:
    - The decrypted word is **"HELLO"**.
---