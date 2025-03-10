#cryptography 

**bcrypt** is a **password hashing function** designed to securely store passwords by transforming them into fixed-length strings ([[#Hash Value]]), making it difficult for attackers to recover the original password.
bcrypt is named after the **Blowfish** cipher, which it is based on. The **"b"** in bcrypt refers to **Blowfish**

---
# Hash Value
A **bcrypt hash** follows the **Modular Crypt Format (MCF)**:
```
$<version>$<cost>$<salt><hash>
```
Example:
```
$2b$12$5vKB5FUiX9ZLqLIVFZ5F6uNHG9PjMg6Y2rQX5he0C6XKjWzLJq9zi
```
1.  **Prefix ($2a$, $2b$, $2y$)**
	This specifies the **bcrypt version** used:
	- `$2a$` – Original bcrypt version (1999)
	- `$2b$` – Current recommended version (fixes security issues in `$2a$`)
	- `$2y$` – Specific to OpenBSD
	Most modern implementations use **`$2b$`**.
2. **Cost Factor (Work Factor)**
	This is a **two-digit number** (e.g., `12` in `$2b$12$...`) that determines how many times the hashing function is applied.
	- **Higher cost = more computational work**
	- The number of iterations is `2^cost`.
	    - Example:
	        - Cost **10** → `2^10 = 1024` iterations
	        - Cost **12** → `2^12 = 4096` iterations
	- Increasing the cost over time makes bcrypt resistant to **Moore’s Law** (i.e., improving hardware speed).
3. **Salt (22 characters)**
	- A **randomly generated 16-byte salt**, encoded in **Base64** (22 characters long).
	- Ensures that **identical passwords produce different hashes** to prevent precomputed attacks (rainbow tables).
4. **Hash (31 characters)**
	- The final **23-byte hashed password**, encoded in **Base64** (31 characters).
	- Derived using the **Blowfish cipher** in a **key-expansion loop**.

---
# **How bcrypt works**
1. **Generate a Salt** - A **16-byte random salt** is created.
2. **Apply the Work Factor** - The password + salt undergo `2^cost` rounds of **Blowfish key expansion**.
3. **Derive the Hash** - The resulting key is truncated to **23 bytes** and **Base64-encoded**.
4. **Store the Hash** - The full **60-character bcrypt hash** is saved, including prefix, cost, salt, and hash.
---