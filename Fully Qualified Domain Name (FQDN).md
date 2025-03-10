#networking 

A **FQDN** is a **complete and exact address** of a website or a server on the internet in a human readable format instead of [[Internet Protocol address (IP address)|IP Address]]. It includes:
```php
`<hostname>.<subdomain>.<domain>.<TLD>`
```
1. **[[Hostname]]** (specific computer or machine)
2. **Subdomain** (A section of `<domain>`)
3. **[[Domain name]]** (website or organization)
4. **[[Top-level domain (TLD)]]** (like `.com`, `.org`, `.net`)

**Examples of an FQDN**
- **`www.sales.example.com`**
    - `www` → **Hostname**
    - **`sales`** → **Subdomain** (A section of `example.com`, like a department)
    - `example` → **Domain Name**
    - `.com` → **TLD**
- **`mail.google.com`**
    - `mail` → Hostname
    - `google` → Domain Name
    - `.com` → TLD
---
### **How to check FDQN**
``` bash
#Linux/Mac
hostname -f 
hostname --fqdn
```
### **FQDN vs. Normal Domain**
- `google.com` → **Not an FQDN** (just a domain name)
- `www.google.com` → ✅ **FQDN** (complete address)
---