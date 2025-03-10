#command 

The **`openssl`** command is used for working with [[Secure Sockets Layer (SSL)|SSL]]/[[Transport Layer Security (TLS)|TLS]] protocols and performing cryptographic tasks, such as generating keys, creating certificates, managing certificates, encrypting/decrypting data, and more. It is widely used for testing and managing security-related tasks.

```sh
openssl <command> [options]
```
- `<command>` is the operation or action you want to perform (e.g., `genpkey`, `req`, `x509`, etc.).
- `[options]` are additional flags or arguments that modify the behavior of the command.

---
# **Options**
- **`-in`**: Input file.
- **`-out`**: Output file.
- **`-key`**: The private key file.
- **`-days`**: Validity period of a certificate (in days).
- **`-text`**: Print detailed information.
- **`-pubin`**: Input is a public key.
- **`-passin`**: Passphrase for the private key input.
- **`-passout`**: Passphrase for the private key output.
- **`-nodes`**: Do not encrypt the private key (no passphrase).
# **Usage**
#### **1. Generate a Private Key**
To generate a private key (for RSA, in this example):
```sh
openssl genpkey -algorithm RSA -out private_key.pem
```
- **`genpkey`**: Command to generate a private key.
- **`-algorithm RSA`**: Specifies the algorithm to use (RSA in this case).
- **`-out private_key.pem`**: The output file where the private key will be saved.
#### **2. Generate a Public Key from a Private Key**
Once you have a private key, you can derive the corresponding public key:
```sh
openssl rsa -pubout -in private_key.pem -out public_key.pem
```
- **`rsa`**: Command to work with RSA keys.
- **`-pubout`**: Indicates that the output should be the public key.
- **`-in private_key.pem`**: The input private key file.
- **`-out public_key.pem`**: The output public key file.
#### **3. Create a Self-Signed Certificate**

A **self-signed certificate** can be created directly from the private key:

```sh
openssl req -new -x509 -key private_key.pem -out cert.pem -days 365
```

- **`req`**: Command for generating a certificate signing request (CSR) and self-signed certificates.
- **`-new`**: Creates a new request.
- **`-x509`**: Indicates that you want a self-signed certificate (instead of a CSR).
- **`-key private_key.pem`**: The private key to use for signing.
- **`-out cert.pem`**: The output certificate file.
- **`-days 365`**: Validity period of the certificate (in days).

#### **4. View the Contents of a Certificate**

You can view details of a certificate with the `x509` command:

```sh
openssl x509 -in cert.pem -text -noout
```

- **`x509`**: Command to manage certificates.
- **`-in cert.pem`**: Input certificate file.
- **`-text`**: Display the certificate details in human-readable format.
- **`-noout`**: Don't output the encoded version of the certificate.

#### **5. Create a Certificate Signing Request (CSR)**

A CSR is often required when you want to get a certificate from a Certificate Authority (CA):

```sh
openssl req -new -key private_key.pem -out csr.pem
```

- **`req`**: Command for generating certificate requests.
- **`-new`**: Create a new request.
- **`-key private_key.pem`**: The private key to associate with the CSR.
- **`-out csr.pem`**: The output CSR file.

#### **6. Verify a Certificate**

You can verify if a certificate is valid and properly signed by its corresponding private key:

```sh
openssl verify cert.pem
```

- **`verify`**: Command to verify a certificate.
- **`cert.pem`**: The certificate file to verify.

#### **7. Encrypt Data Using Public Key**

You can use a public key to encrypt data (the recipient would use their private key to decrypt it):

```sh
openssl rsautl -encrypt -inkey public_key.pem -pubin -in plaintext.txt -out encrypted.dat
```

- **`rsautl`**: Command for RSA encryption and decryption.
- **`-encrypt`**: Indicates encryption mode.
- **`-inkey public_key.pem`**: The public key to use for encryption.
- **`-pubin`**: Indicates that the input key is a public key.
- **`-in plaintext.txt`**: Input plaintext file.
- **`-out encrypted.dat`**: The output encrypted file.

#### **8. Decrypt Data Using Private Key**

To decrypt the data encrypted with the public key:

```sh
openssl rsautl -decrypt -inkey private_key.pem -in encrypted.dat -out decrypted.txt
```

- **`rsautl`**: Command for RSA encryption and decryption.
- **`-decrypt`**: Indicates decryption mode.
- **`-inkey private_key.pem`**: The private key to use for decryption.
- **`-in encrypted.dat`**: The encrypted file.
- **`-out decrypted.txt`**: The output decrypted file.

#### **9. Convert Certificate Formats (e.g., PEM to DER)**

You can convert certificates from one format to another (e.g., from PEM to DER):

```sh
openssl x509 -in cert.pem -outform DER -out cert.der
```

- **`x509`**: Command for working with X.509 certificates.
- **`-in cert.pem`**: Input PEM certificate file.
- **`-outform DER`**: Specifies the output format (DER in this case).
- **`-out cert.der`**: The output DER certificate file.

#### **10. Generate a Random Number (for Keys or Passwords)**

You can generate random numbers or strings for keys or passwords:

```sh
openssl rand -base64 32
```

- **`rand`**: Command to generate random numbers.
- **`-base64`**: Encode the output in Base64.
- **`32`**: The number of bytes (will output a 256-bit random value).

#### **11. Check the Integrity of a Certificate (Hashing)**

You can check the integrity or hash of a certificate:

```sh
openssl dgst -sha256 cert.pem
```

- **`dgst`**: Command for generating message digests (hashes).
- **`-sha256`**: Specifies the hash algorithm to use (SHA-256 in this case).
- **`cert.pem`**: The certificate file to hash.

---



---
# **Installation**
```bash
sudo apt install openssl
sudo dnf install openssl
sudo yum install openssl
sudo pacman -S openssl
brew install openssl
```
