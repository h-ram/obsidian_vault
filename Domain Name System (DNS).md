#networking #draft 

DNS is a system that translates a **[[Domain Name]]** (like `example.com`) into **[[Internet Protocol address (IP address)|IP address]]** (like `192.168.1.1`) that computers use to identify each other on the internet.
DNS makes the internet easier to navigate by letting you use human-friendly names instead of numeric IPs.
### How DNS Works:
1. **You enter a domain name** (e.g., `www.google.com`) into your browser.
2. **DNS Resolver:**
	- The **[[DNS resolver]]** (usually provided by your [[Internet Service Provider (ISP)]]) is the first place it checks. If it has recently looked up the address, it might already know the IP address and can return it right away. This is called **caching**.
3. **Querying the DNS Root Server**
	- If the resolver doesn’t have the cached result, it sends a **DNS query** to one of the **root DNS servers**.
	- The root servers don't know the exact IP address for `www.example.com`, but they can direct the query to a **Top-Level Domain (TLD) server** based on the domain’s extension (e.g., `.com`, `.org`, `.net`).
 4. **TLD Name Servers**
	- The TLD server knows the authoritative DNS servers for the domain. For example, for `www.example.com`, the `.com` TLD server knows the authoritative name servers that are responsible for `example.com`.
	- The resolver then sends a query to one of these **authoritative name servers** for `example.com`.
5. **Authoritative DNS Server**
	- The **authoritative DNS server** for `example.com` holds the actual [[DNS Record|DNS Records]] for that domain, including **A records**, **MX records**, and other types of records.
	- The authoritative server responds to the DNS query with the **IP address** for `www.example.com` (e.g., `93.184.216.34`).
6. **Caching the IP Address**
	- The **DNS resolver** then returns the IP address to your web browser, which can now connect to the website.
	- Your browser also caches the result for a short period, so it doesn’t need to ask DNS servers again for the same domain in the future.
7. **Connecting to the Website**
	- Now that your browser has the correct IP address, it can send a request to the server at that IP (the web server hosting `example.com`).
	- The web server responds, and your browser loads the website!