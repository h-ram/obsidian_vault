#done

A **digital signature** is a string of text used to verify the authenticity of digital messages or documents.it ensures that a document has not been altered and was signed by a specific entity.
# **How It Works**
1. **Hashing:** The document is hashed using a cryptographic hash function (e.g., SHA-256).
2. **Encryption:** The hash is encrypted with the sender’s private key, creating the digital signature. Then it is sent alongside the raw document.
3. **Verification:** The recipient decrypts the signature using the sender’s public key and compares it to the hash of the received document. If they match, the document is authentic. (the recipient can get the public key from different places, it doesn't concernt this page)

**Example**
Suppose the document contains:
```
"Transfer $1000 to Alice"
```
1. **Hashing the Document** (e.g Applying **SHA-256** hashing)
	```
    f2ca1bb6c7a9a2e8f1c6773b7cdb6a5f9e8f5b87c5b1b7a54c53eb1dfb8919a0
    ```
2. **Encrypting the Hash with the Private Key (Signing)** (e.g using RSA)
	```
	MEUCIQCl1N9b3z34xVv0O23BhL2J1Lp8JTPZ0sQ/1jNKh7v0FgIgOGQdo5HwAXLh
	UhzNk6L3mFJ0Ku2M8K9KLOqGk/5GTLM=
	```
3. **Verification Using the Public Key**
When the recipient receives the signed document, they:
	1. **Extract the digital signature** from the document.
	2. **Decrypt it** using the sender’s **public key** (available in their digital certificate).
	3. **Recalculate the document’s hash** and compare it with the decrypted hash.
	- If **both hashes match**, the document is **authentic and unaltered**.
	- If **they don’t match**, the document has been **modified or is from an untrusted source**.
# **What It Looks Like**
A digital signature typically appears as a **long string of characters**, often in hexadecimal or Base64 encoding. Example:
```
MEUCIQCl1N9b3z34xVv0O23BhL2J1Lp8JTPZ0sQ/1jNKh7v0FgIgOGQdo5HwAXLh
UhzNk6L3mFJ0Ku2M8K9KLOqGk/5GTLM=
```
---