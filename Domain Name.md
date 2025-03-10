#networking 

A **domain name** is a human-readable address used to identify a device on the internet instead of the raw [[Internet Protocol address (IP address)|IP address]].
**Example**: `amazon.com`, `mail.google.com`, `twitch.tv`
A domain name can contain a domain and a top-level domain (evilcorp.com) or a sub-domain followed by a domain and top-level domain (tryhackme.evilcorp.com)

---
### How Domain Names Work
When you type a domain name (like `www.google.com`) into your browser, the **[[Domain Name System (DNS)]]** translates that domain name into the corresponding IP address (`172.217.9.78`) so that your browser can connect to the correct server hosting the website.
### Parts of a Domain Name:
1. **Top-Level Domain (TLD)**: The part after the last dot (e.g., `.com`, `.org`, `.net`, `.edu`).
    - **Generic TLDs (gTLDs)**: Common examples include `.com`, `.org`, `.net`, `.gov`.
    - **Country Code TLDs (ccTLDs)**: Specific to countries, like `.us` (United States), `.uk` (United Kingdom), `.de` (Germany).
2. **Second-Level Domain (SLD)**: The part just before the TLD. This is often the name of the website or organization (e.g., `google`, `wikipedia`, `bbc`).
3. **Subdomain**: Optional, and placed before the second-level domain. Subdomains help organize different sections of a website (e.g., `blog.example.com`, `shop.example.com`).