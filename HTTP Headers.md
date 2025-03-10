#networking 

HTTP **headers** are key-value pairs that are sent with both requests and responses, providing metadata about the message. (They are not case-sensitive)

---
There are 5 types of headers:
1. **[[#General Headers]]** used in both HTTP requests and responses to describe the message rather than its contents.
2. **[[#Entity Headers]]** common to both the request and response. used to describe the content (entity) transferred by a message.
3. **[[#Request Headers]]** used in an HTTP request and do not relate to the content of the message.
4. **[[#Response Headers]]** used in an HTTP response and do not relate to the content
5. **[[#Security Headers]]** a class of response headers used to specify certain rules and policies to be followed by the browser while accessing the website.
---
### General Headers
* `Date` -> Date and time where message was sent
* `Connection` -> Dictates if the current network connection should stay alive after the request finishes. (`close`, `keep-alive`)
```yaml
Date: Wed, 16 Feb 2022 10:38:44 GMT
Connection: close
```
###  Entity Headers
- `Content-Type` -> describe the type of resource being transferred. (json, text, ..etc)
- `Content-Length` the size of the entity being passed in **Bytes**
- `Content-Encoding` type of compression.
- `Media-Type` -> similar to `Content-Type`, and describes the data being transferred.
- `Boundary` -> a marker to separate content when there is more than one in the same message.

```yaml
Content-Type: text/html
Content-Length: 385
Content-Encoding: gzip
boundary="b4e4fbd93540"
Media-Type: application/pd
```
###  Request Headers
- `Host` -> can be a domain name or an IP address to the host that has the resource.
- `User-Agent` -> client information (browser, browser version, operating system)
- `Referer` -> where the current request is coming from, (clicked a link or searched)
- `Accept` -> which media types the client can understand.
- `Cookie` -> Contains cookie-value pairs
- `Authorization` -> method for the server to identify clients. (using a token or ..etc)
```yaml
Host: www.inlanefreight.com
User-Agent: curl/7.77.0
Referer: http://www.inlanefreight.com/
Accept: */*
Cookie: PHPSESSID=b4e4fbd93540
Authorization: BASIC cGFzc3dvcmQK
```
###  Response Headers
- `Server` -> information about the HTTP server, which processed the request. (version ..etc)
- `Set-Cookie` -> cookie-value pair that tells the client to save a cookie.
- `WWW-Authenticate` -> Notifies the client about the type of authentication required to access the requested resource.
```yaml
Server: Apache/2.2.14 (Win32)
Set-Cookie: PHPSESSID=b4e4fbd93540
WWW-Authenticate: BASIC realm="localhost"
```
### Security Headers
- `Content-Security-Policy` -> This header instructs the browser to accept resources only from certain trusted domains.
- `Strict-Transport-Security` -> Prevents the browser from accessing the website over the plaintext HTTP protocol, and forces all communication to be carried over the secure HTTPS protocol.
- `Referrer-Policy` -> Dictates whether the browser should include the value specified via the `Referer` header or not.
```yaml
Content-Security-Policy: script-src 'self'
Strict-Transport-Security: max-age=31536000
Referrer-Policy: origin
```