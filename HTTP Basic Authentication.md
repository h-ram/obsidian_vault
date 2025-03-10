#networking 

It is a straightforward method for a client to authenticate itself to a server by sending a username and password with each HTTP request. This is done in two different ways:
1. in the URL : `https://username:password@example.com`
2. in the Authentication header: `Authentication: Basic dXNlcm5hbWUgcGFzc3dvcmQ=` , The username and password are encoded in [[Base64]].
If the authentication failed, the response will contain a `www-authentication` header that indicates that `Basic` authentication is required, and it also includes a **realm** name to indicate which set of credentials is required.
```
NOTE: including username:password in the URL will automatically create an Authentication header with the base64 encoding of (username:password)
```
---
**Example Requests**
```http
# http://example.com

GET /protected-resource HTTP/1.1 
Host: example.com

HTTP/1.1 401 Unauthorized 
WWW-Authenticate: Basic realm="Admin Area"

```

```http
# http://admin:admin@example.com

GET /protected-resource HTTP/1.1
Host: example.com 
Authorization: Basic YWRtaW46YWRtaW4=

HTTP/1.1 200 OK 
Content-Type: text/plain 

Welcome, admin! You have access to this resource.
```
---