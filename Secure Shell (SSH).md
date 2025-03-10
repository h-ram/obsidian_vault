 #networking

SSH is a network protocol that runs on port `22` by default and provides users such as system administrators a secure way to access a computer remotely.
### **SSH Authentication Methods**
1. **Password-Based Authentication**
	- The user enters a password to authenticate.
	- Less secure since passwords can be guessed or brute-forced.
2. **Public Key Authentication**
	- Uses a key pair:
	    - **Public Key** (stored on the server)
	    - **Private Key** (kept on the client)
	- The client proves identity by decrypting a challenge using the private key.
	- Much more secure than passwords.
3. **Multi-Factor Authentication (MFA)**
	- Requires an additional authentication factor (e.g., OTP, biometrics).
	- Adds an extra layer of security.
---
Related: [[ssh.sh]]