#cryptography 

> [!NOTE] NOTE
> SSL has been completly replaced with [[Transport Layer Security (TLS)|TLS]] in most applications, many systems and applications refer to SSL when they actually use TLS.

A cryptographic protocol designed to secure communication over a network between a client (e.g., a web browser) and a server (e.g., a website).
### **SSL vs [[Transport Layer Security (TLS)|TLS]]**
- SSL has been replaced by TLS (**Transport Layer Security**), which is more secure and efficient.
- SSL 3.0 was the last version of SSL before it evolved into TLS 1.0.
- **TLS 1.2 and TLS 1.3** are the current secure versions used today.
---
# **SSL Versions**
1. **SSL 1.0**:
    - **Released**: 1995 (never publicly released).
    - **Description**: This was the first version of SSL developed by Netscape. It had major security flaws and was never publicly used.
2. **SSL 2.0**:
    - **Released**: 1995.
    - **Description**: SSL 2.0 was the first publicly released version. However, it had several security weaknesses and was soon replaced by SSL 3.0.
    - **Vulnerabilities**: Weak message authentication, problems with key exchange, and the possibility of downgrade attacks.
3. **SSL 3.0**:
    - **Released**: 1996.
    - **Description**: SSL 3.0 fixed several issues found in SSL 2.0, but it also had significant vulnerabilities that made it less secure.
    - **Vulnerabilities**: Vulnerable to attacks like POODLE (Padding Oracle On Downgraded Legacy Encryption) and cipher block chaining (CBC) weaknesses.

SSL was eventually replaced by **TLS (Transport Layer Security)**, which is more secure and still in use today.
1. **TLS 1.0**:
    - **Released**: 1999.
    - **Description**: TLS 1.0 is based on SSL 3.0, but it includes more secure cryptographic algorithms and fixes for some of SSL's flaws.
    - **Vulnerabilities**: Still has some weaknesses, especially with older ciphers and lack of forward secrecy.
2. **TLS 1.1**:
    - **Released**: 2006.
    - **Description**: TLS 1.1 improved upon TLS 1.0 with better protection against certain attacks, like cipher-block chaining (CBC) attacks.
    - **Vulnerabilities**: Still vulnerable to some types of attacks (e.g., padding oracle attacks), and it has been largely deprecated in favor of TLS 1.2.
3. **TLS 1.2**:
    - **Released**: 2008.
    - **Description**: TLS 1.2 brought significant improvements in security, including support for stronger encryption algorithms, and it is widely adopted.
    - **Vulnerabilities**: Fewer vulnerabilities than earlier versions, though issues like BEAST (Browser Exploit Against SSL/TLS) were mitigated in later updates.
4. **TLS 1.3**:
    - **Released**: 2018.
    - **Description**: TLS 1.3 is the latest version and includes more robust security features, such as forward secrecy and the removal of obsolete cryptographic algorithms. It reduces handshake latency and improves overall performance.
    - **Vulnerabilities**: Much more secure than earlier versions, though still not immune to future vulnerabilities as cryptography advances.
### **SSL/TLS Versions Summary**
- **SSL 1.0**: Never released publicly.
- **SSL 2.0**: Weak and obsolete, deprecated.
- **SSL 3.0**: Obsolete, vulnerable to POODLE and other attacks.
- **TLS 1.0**: Successor to SSL 3.0, deprecated.
- **TLS 1.1**: Deprecated.
- **TLS 1.2**: Still widely used and recommended.
- **TLS 1.3**: Current standard, more secure and efficient.
---
### **Which Version to Use?**
- **TLS 1.2** and **TLS 1.3** are the recommended protocols for secure communications today. SSL and earlier TLS versions (1.0, 1.1) are deprecated due to known vulnerabilities.
- **TLS 1.3** should be prioritized, as it offers improved security and performance over **TLS 1.2**.


**SSL (Secure Sockets Layer)** is a cryptographic protocol designed to provide secure communication over a computer network. Although SSL has been largely replaced by **TLS (Transport Layer Security)**, understanding SSL is still important for historical context, as many systems and applications still use SSL or refer to SSL when they actually use TLS.
SSL and TLS both work in a similar manner, but TLS is the more secure and modern version. Below, I'll explain how SSL works in detail:
### **Overview of SSL:**
SSL is designed to establish a secure, encrypted communication channel between two systems (typically a client and a server). SSL operates between the transport layer (TCP/IP) and the application layer (e.g., HTTP), allowing protocols such as HTTP (resulting in HTTPS) to be securely transmitted.
SSL relies on both **symmetric encryption** (for fast communication) and **asymmetric encryption** (for secure key exchange). It also provides mechanisms for **authentication** and **integrity**.

---

# **SSL Handshake**
When a client (e.g., a web browser) wants to connect securely to a server (e.g., a website), an SSL handshake takes place. This is the process where both parties agree on encryption settings and exchange necessary keys.
The SSL handshake consists of the following steps:

---
#### **1. Client Hello**
- **Purpose**: The client initiates the SSL connection by sending a "ClientHello" message to the server.
- **Contents**:
    - **SSL version** (e.g., SSL 3.0 or SSL 2.0).
    - **Cipher suites** supported by the client (a list of encryption algorithms the client can use).
    - **Random number**: A value to help create a unique session key.
    - **Session ID** (if resuming a previous session).
#### **2. Server Hello**
- **Purpose**: The server responds to the "ClientHello" with a "ServerHello" message.
- **Contents**:
    - **SSL version**: The version of SSL/TLS the server chooses (from the list provided by the client).
    - **Cipher suite**: The chosen cipher suite for the connection (from the list provided by the client).
    - **Server's random number**: Another random value for generating the session key.
    - **Session ID**: If the server is willing to resume a session, it includes the session ID.
#### **3. Server Certificate**
- **Purpose**: The server sends its **digital certificate** (SSL certificate) to the client.
- **Contents**:
    - The server’s **public key**: Part of the asymmetric encryption system.
    - The server’s **certificate authority (CA) signature**: Proves that the server's certificate is legitimate.
    - The certificate also contains information about the server’s identity, domain name, and validity period.
#### **4. Key Exchange**
- **Purpose**: The client and server establish a shared **session key** for symmetric encryption.
    - In **SSL v3**, the server might generate a **pre-master secret** and send it encrypted with the client’s public key.
    - In **SSL v2**, a less secure method of key exchange is used.
#### **5. Client Finished**
- **Purpose**: The client sends a message indicating that it is ready to proceed.
    - This message is encrypted using the session key that both the client and server agreed upon in the previous steps.
#### **6. Server Finished**
- **Purpose**: The server sends a message indicating that it is ready to proceed.
    - This message is also encrypted with the session key.
At this point, both the client and server have securely established a session with a shared session key, and they can communicate securely using symmetric encryption.

---

### **Encryption and Data Integrity**

Once the SSL handshake is complete, the client and server use **symmetric encryption** to encrypt the data they exchange. This is because symmetric encryption is much faster than asymmetric encryption. They use the **session key** derived during the handshake for encryption.

#### **Symmetric Encryption:**

- Both the client and server use the same key for encryption and decryption.
- **AES (Advanced Encryption Standard)** is commonly used for this encryption, providing confidentiality.

#### **Data Integrity:**

- SSL also uses **Message Authentication Codes (MACs)** to ensure data integrity.
- Each message includes a MAC to ensure that data hasn't been altered during transmission.

---

### **Certificate Validation (Authentication)**

During the handshake, the client validates the server's SSL certificate to ensure it is trusted. This process involves the following:

1. **Checking the certificate’s validity**:
    - Ensuring that the certificate is not expired.
    - Checking that the certificate is issued by a trusted Certificate Authority (CA).
    - Verifying the certificate’s domain matches the server's domain (e.g., the certificate for `example.com` cannot be used on `test.com`).
2. **Checking the CA signature**:
    - The client verifies the digital signature on the certificate using the CA’s public key. This confirms that the certificate was issued by a trusted CA.

---

### **SSL Record Layer (Data Transmission)**

After the handshake is complete, all data between the client and server is encrypted and transmitted using SSL's **Record Layer**. This layer ensures the data remains secure, authenticated, and intact during transmission.

The **Record Layer** performs the following tasks:

- **Segmentation**: Data is divided into smaller chunks for transmission.
- **Encryption**: Data is encrypted using the session key.
- **Integrity Checking**: A MAC is added to each message to ensure its integrity.

---

### **Closing the SSL/TLS Connection**

To terminate the SSL session, the client and server perform a **closure alert**. This alerts the other party that no more data will be transmitted, and both sides close the connection securely.

---
### **Summary of SSL Working**
1. **Client Hello**: Client initiates the connection, sending its supported protocols and cipher suites.
2. **Server Hello**: Server responds with its chosen protocol and cipher suite, along with its digital certificate.
3. **Key Exchange**: Client and server exchange data to securely generate a shared session key.
4. **Encryption**: Data is encrypted using the session key and transmitted with integrity checks (MACs).
5. **Authentication**: The client validates the server’s certificate to ensure it is authentic.
6. **Secure Communication**: Both parties exchange secure, encrypted data.
7. **Closure**: The session ends with a closure alert, ensuring the connection is properly terminated.

---
### **Note:**
SSL is deprecated in favor of **TLS**, which is more secure. The SSL protocols, especially SSL v2 and v3, have been found to have various vulnerabilities. TLS 1.2 and 1.3 are the recommended protocols for secure communication today.
Let me know if you need more clarification or examples!
# **Resources**
- https://www.youtube.com/watch?v=67Kfsmy_frM&ab_channel=Sematext