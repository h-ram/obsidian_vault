#networking 

DNS records are used to map [[Domain Name System (DNS)|domain names]] to [[Internet Protocol address (IP address)|IP addresses]] and other data. 
A **DNS record** is a database entry in the Domain Name System (DNS) that provides information about a domain, such as its associated IP address, mail server, or other services.
# Types of DNS Records
1. **A (Address) Record**: Maps a domain to an IPv4 address. 
2. **AAAA (IPv6 Address) Record**: Maps a domain to an IPv6 address.
3. **CNAME (Canonical Name) Record**: Maps a domain name to another domain name (alias).
4. **MX (Mail Exchange) Record**: Specifies mail servers for a domain.
5. **TXT (Text) Record**: Holds arbitrary text, often used for verification (e.g., SPF records).
6. **NS (Name Server) Record**: Specifies authoritative DNS servers for a domain.
7. **PTR (Pointer) Record**: Maps an IP address to a domain name (reverse DNS lookup).
8. **SOA (Start of Authority) Record**: Indicates the start of a zone and provides information about the domain.
9. **SRV (Service) Record**: Specifies services available in a domain (e.g., for SIP or XMPP).

```php
example.com. IN A 192.0.2.1

example.com. IN AAAA 2001:0db8:85a3:0000:0000:8a2e:0370:7334
    
www.example.com. IN CNAME example.com.
    
example.com. IN MX 10 mail.example.com.
    
example.com. IN TXT "v=spf1 include:_spf.example.com ~all"
    
example.com. IN NS ns1.example.com.
    
1.2.0.192.in-addr.arpa. IN PTR example.com.
    
example.com. IN SOA ns1.example.com. hostmaster.example.com. (2025020101 3600 1800 1209600 86400)
    
_sip._tcp.example.com. IN SRV 10 60 5060 sipserver.example.com.
```
# General DNS Record Format:
```php
<name> <TTL> <class> <type> <value>
```
- **`<name>`**: The domain or subdomain the record applies to (e.g., `www.example.com` or `example.com`).
- **`<TTL>`** (Time to Live): The duration (in seconds) that the record should be cached by resolvers (e.g., `3600` seconds or 1 hour).
- **`<class>`**: Usually "IN" (stands for Internet), this is typically fixed.
- **`<type>`**: The type of DNS record (e.g., `A`, `MX`, `CNAME`).
- **`<value>`**: The value or data for that record (e.g., an IP address, mail server).
```php
www.example.com. 3600 IN CNAME example.com.
```

