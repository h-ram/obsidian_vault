### **What is Encoding?**
Encoding is the process of converting **data** from one format to another. In the context of text, encoding typically means converting **characters (human-readable text) into binary (machine-readable format)** using a specific character set.

Encoding is necessary because computers only understand **binary (0s and 1s)**, so text and symbols need to be transformed into a format that computers can process and store.

---
## **Types of Encoding**
Encoding can be categorized into different types based on its purpose:
### **1. Character Encoding (Text Encoding)**
- Converts **human-readable characters** into **binary data** (bytes).
- Used in text processing, web pages, files, and data transmission.
#### **Common Character Encodings**

|Encoding|Description|
|---|---|
|**ASCII**|Oldest encoding, supports only English letters and basic symbols (0-127).|
|**UTF-8**|Most widely used; supports all Unicode characters; variable-length encoding (1-4 bytes per character).|
|**UTF-16**|Uses 2 or 4 bytes per character; supports all Unicode characters.|
|**UTF-32**|Uses a fixed 4 bytes per character; supports all Unicode characters.|
#### **Example: UTF-8 Encoding**
Let's encode the word **"Hello"** into **UTF-8**:

```python
text = "Hello"
encoded_text = text.encode('utf-8')
print(encoded_text)  # Output: b'Hello'
```

Here, each character in `"Hello"` is converted into a sequence of **bytes**.

---
### **2. [[Base64]] Encoding**
- Converts **binary data** into a **text format** (using 64 printable characters).
- Used for encoding **images, files, or other binary data** in text-based protocols like emails, JSON, or URLs.
#### **Example: Base64 Encoding**

```python
import base64

data = "Hello"
encoded_data = base64.b64encode(data.encode('utf-8'))
print(encoded_data)  # Output: b'SGVsbG8='
```
- `"Hello"` → Base64 encoded as `"SGVsbG8="`.
- This is **not encryption**; it’s just a way to represent binary data using printable characters.
---
### **3. URL Encoding**
- Converts special characters in a URL into a **safe format** (percent encoding).
- Spaces become `%20`, special symbols get converted to `%XX` (hex representation).
#### **Example: URL Encoding**
```python
import urllib.parse

text = "Hello World!"
encoded_url = urllib.parse.quote(text)
print(encoded_url)  # Output: 'Hello%20World%21'
```
---
### **4. Binary Encoding**
- Converts text into **binary (0s and 1s)**.
#### **Example:**

The character **'A'** in **ASCII** → `01000001` (binary).
```python
text = "A"
binary = ' '.join(format(ord(char), '08b') for char in text)
print(binary)  # Output: '01000001'
```
---
## **Why is Encoding Important?**
1. **Data Storage & Transmission** – Text needs to be encoded before saving in files or databases.
2. **Internationalization** – UTF-8 allows global character support (e.g., Chinese, Arabic, emojis).
3. **Compatibility** – Proper encoding ensures text works across different systems (Windows, Linux, macOS).
4. **Security** – Encoding (like Base64, URL encoding) prevents data corruption in transmission.
---
## **Encoding vs. Encryption vs. Hashing**

|**Concept**|**Purpose**|**Reversible?**|**Example**|
|---|---|---|---|
|**Encoding**|Convert data into a different format for compatibility.|✅ Yes|Base64, UTF-8, ASCII|
|**Encryption**|Protect data using a secret key.|✅ Yes (with the key)|AES, RSA|
|**Hashing**|Convert data into a fixed-length fingerprint.|❌ No|SHA-256, MD5|

---
