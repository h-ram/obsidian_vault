#command #networking 

cURL (Client URL) is used to transfer data to or from a server using URLs.
```php
curl [options] [URL]

-X, --request      | GET, POST, PUT, DELETE 
-d, --data         | "name=John&age=30"
-H, --header       | "Content-Type: application/json"
-u, --user         | username:password
-I, --head         | #Fetch only the HTTP headers
-o, --output       | #Save response to a file
-O, --remote-name  | #Save response as the original filename
-L, --location     | #Follow redirects
-v, --verbose      | 
-k, --insecure     | #Allow connections to SSL sites without certificates
--data-urlencode   | #URL-encode data in a POST request
--proxy            | #Use a proxy server
-s --silent        | #Silence all status messages in terminal.
```
# **Options**

| **Option**            | **Description**                                                         |
| --------------------- | ----------------------------------------------------------------------- |
| `-X`, `--request`     | Specifies the HTTP method (e.g., `GET`, `POST`, `PUT`, `DELETE`).       |
| `-d`, `--data`        | Sends data in the request body (used with `POST` requests).             |
| `-H`, `--header`      | Adds a custom header to the request.                                    |
| `-L`, `--location`    | Follows redirects automatically (e.g., `301`, `302`).                   |
| `-i`, `--include`     | Includes HTTP response headers in the output.                           |
| `-O`, `--remote-name` | Downloads a file and saves it with its original filename.               |
| `-o`, `--output`      | Saves the response to a file with a specified name.                     |
| `-u`, `--user`        | Sends credentials for HTTP Basic Authentication (username:password).    |
| `-I`, `--head`        | Fetches only the headers (not the body) of a URL.                       |
| `-v`, `--verbose`     | Verbose mode; shows detailed request and response information.          |
| `-k`, `--insecure`    | Allows connections to SSL sites without certificates (insecure).        |
| `-F`, `--form`        | Sends data in the form of `multipart/form-data` (file upload).          |
| `-s`, `--silent`      | Suppresses progress meter and error messages.                           |
| `-w`, `--write-out`   | Displays information about the request and response (e.g., time).       |
| `-A`, `--user-agent`  | Specifies the `User-Agent` header to use in requests.                   |
| `-b`, `--cookie`      | Sends a cookie with the request.                                        |
| `-c`, `--cookie-jar`  | Saves cookies to a file.                                                |
| `-T`, `--upload-file` | Uploads a file to the specified URL.                                    |
| `-n`, `--netrc`       | Uses `.netrc` for automatic authentication.                             |
| `-z`, `--time-cond`   | Makes a request based on modification time (e.g., `If-Modified-Since`). |
| `-e`, `--referer`     | Sends a `Referer` header in the request.                                |
| `-p`, `--post301`     | Enables automatic POST requests on redirect.                            |

---
# **Usage**
### **Basic Request**
```bash
$ curl inlanefreight.com
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
...SNIP...
```
This sends a simple GET request to `https://www.example.com` and prints the response body to the terminal.
### **Post Request**
```bash
curl -X POST -d "name=John&age=30" https://www.example.com
```
- Sends data in the body of the POST request (typically used for forms or APIs).
1. **-H or --header**: Set custom headers:
    ```bash
    curl -H "Content-Type: application/json" https://www.example.com
    ```
    - Used for setting headers, such as content type or authentication tokens.
2. **-u or --user**: Basic Authentication:
### **Basic Authentication**
```bash
$ curl -u username:password https://www.example.com
$ curl https://username:password@www.example.com
```
- Pass a username and password for HTTP basic authentication.
1. **-I or --head**: Fetch only the HTTP headers:
    ```bash
    curl -I https://www.example.com
    ```
    - This returns only the headers, not the body of the response (useful for inspecting response codes, etc.).
2. **-o or --output**: Save response to a file:
    ```bash
    curl -o file.txt https://www.example.com
    ```
    - Saves the response content to a file (e.g., `file.txt`).
3. **-O or --remote-name**: Save response as the original filename:
    ```bash
    curl -O https://www.example.com/file.zip
    ```
    - Downloads the file and saves it with its original filename (e.g., `file.zip`).
4. **-L or --location**: Follow redirects:
    ```bash
    curl -L https://www.example.com
    ```
    - If the URL redirects to another URL (e.g., `301` or `302`), this option tells cURL to follow the redirect automatically.
5. **-v or --verbose**: Display detailed information about the request and response:
    ```bash
    curl -v https://www.example.com
    ```
    - Useful for debugging, as it shows headers, request/response bodies, and more.
6. **-k or --insecure**: Allow connections to SSL sites without certificates:
    ```bash
    curl -k https://www.example.com
    ```
    - Use this when working with SSL certificates that may be self-signed or not trusted.
7. **--data-urlencode**: URL-encode data in a POST request:
    ```bash
    curl --data-urlencode "name=John Doe" https://www.example.com
    ```
    - Useful for encoding special characters in the URL (e.g., spaces).
8. **--proxy**: Use a proxy server:
    ```bash
    curl --proxy http://proxy.example.com:8080 https://www.example.com
    ```
    - Routes the request through a proxy server.
### Example cURL Use Cases:
9. **GET Request**:
    ```bash
    curl https://api.example.com/data
    ```
    - Retrieves data from the API and prints the response.
10. **POST Request with JSON Data**:
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{"name":"John", "age":30}' https://api.example.com/users
    ```
    - Sends JSON data to the server using the POST method.
11. **Download a File**:
    ```bash
    curl -O https://www.example.com/file.zip
    ```
    - Downloads a file and saves it with the original filename.
12. **Follow Redirects**:
    ```bash
    curl -L https://www.example.com
    ```
    - Follows any redirects (e.g., `301`, `302`) and shows the final destination.
13. **Check Response Headers**:
    ```bash
    curl -I https://www.example.com
    ```
    - Fetches only the headers of the response, not the body.
14. **Download Multiple Files**:
    ```bash
    curl -O https://www.example.com/file1.zip -O https://www.example.com/file2.zip
    ```
    - Downloads multiple files.
### Advanced cURL Features:
15. **Sending Files with cURL**:
    - You can upload files using the `-F` flag:
	```bash
    curl -X POST -F "file=@/path/to/file" https://www.example.com/upload
	```
- This sends the file as a form field named `file`.
16. **Multipart Form Data**:
    - You can simulate a form submission with file uploads:
```bash
    curl -X POST -F "name=John" -F "file=@/path/to/file" https://www.example.com/upload
```
17. **Using cURL with APIs**:
    - To interact with RESTful APIs, you often use cURL to send JSON data with POST requests:
```bash
    curl -X POST -H "Content-Type: application/json" -d '{"username":"test", "password":"secret"}' https://api.example.com/login
```
18. **Using cURL with Authentication Tokens**:
    - For APIs that require OAuth tokens or Bearer tokens, you can pass them in the `Authorization` header:
```bash
    curl -H "Authorization: Bearer YOUR_TOKEN_HERE" https://api.example.com/endpoint
```
### Debugging and Logging:
- **Check the Request and Response**:
    ```bash
    curl -v https://www.example.com
    ```
    - The `-v` (verbose) flag provides detailed info, including headers and body content, useful for debugging.
- **Save cURL Output to a File**:
    ```bash
    curl -o response.txt https://www.example.com
    ```
    - Saves the response body into a file called `response.txt`.
### cURL in Scripts:
cURL is often used in shell scripts to automate tasks like downloading files, testing APIs, or sending data. For example:
```bash
#!/bin/bash
curl -X POST -H "Content-Type: application/json" -d '{"username":"user","password":"pass"}' https://api.example.com/login
```
### Summary of Common cURL Commands:

| Command/Option                  | Description                         |
| ------------------------------- | ----------------------------------- |
| `curl [URL]`                    | Simple GET request                  |
| `curl -X POST [URL]`            | Send a POST request                 |
| `curl -d [data] [URL]`          | Send data with POST request         |
| `curl -H [header] [URL]`        | Set custom headers                  |
| `curl -I [URL]`                 | Fetch headers only                  |
| `curl -o [file] [URL]`          | Save output to a file               |
| `curl -v [URL]`                 | Show detailed information (verbose) |
| `curl -L [URL]`                 | Follow redirects                    |
| `curl -u [user:password] [URL]` | Use basic authentication            |

---
### Supported Protocols
latest version `8.11.1` (`Dec 2024`) supports **28**  protocols.
19. **[[Hypertext Transfer Protocol (HTTP)|HTTP]]** – Standard web protocol (`http://`)
20. **[[Hypertext Transfer Protocol Secure (HTTPS)|HTTPS]]** – Secure web protocol (`https://`)
21. **[[File Transfer Protocol (FTP)|FTP]]** – File Transfer Protocol (`ftp://`)
22. **[[File Transfer Protocol Secure (FTPS)|FTPS]]** – Secure FTP (`ftps://`)
23. **[[SSH File Transfer Protocol|SFTP]]** – SSH File Transfer Protocol (`sftp://`)
24. **SCP** – Secure Copy Protocol (`scp://`)
25. **LDAP** – Lightweight Directory Access Protocol (`ldap://`)
26. **LDAPS** – Secure LDAP (`ldaps://`)
27. **[[Simple Mail Transfer Protocol (SMPT)|SMTP]]** – Simple Mail Transfer Protocol (`smtp://`)
28. **[[Simple Mail Transfer Protocol Secure (SMPTS)|SMTPS]]** – Secure SMTP (`smtps://`)
29. **IMAP** – Internet Message Access Protocol (`imap://`)
30. **IMAPS** – Secure IMAP (`imaps://`)
31. **[[ Post Office Protocol 3 (POP3)|POP3]]** – Post Office Protocol v3 (`pop3://`)
32. **[[Post Office Protocol 3 Secure (POP3S)|POP3S]]** – Secure POP3 (`pop3s://`)
33. **[[Telecommunication Network (TELNET)|TELNET]]** – Command-line interface protocol (`telnet://`)
34. **DICT** – Dictionary server protocol (`dict://`)
35. **GOPHER** – Older web browsing protocol (`gopher://`)
36. **GOPHERS** 
37. **RTMP** – Real-Time Messaging Protocol (`rtmp://`) _(if built with RTMP support)_
38. **RTSP** – Real-Time Streaming Protocol (`rtsp://`)
39. **TFTP** – Trivial File Transfer Protocol (`tftp://`)
40. **FILE** – Access local files (`file://`)
41. **SMB** – Server Message Block (Windows File Sharing) (`smb://`)
42. **SMBS** – Secure SMB (`smbs://`)
43. **MQTT** – Message Queue Telemetry Transport (`mqtt://`)
44. **GEMINI** – Alternative internet protocol (`gemini://`) _(if built with Gemini support)
45. **WS** – WebSocket
46. **WSS** – WebSocket Secure
---
# **Installation**
```sh
sudo apt install curl
sudo dnf install curl
sudo yum install curl
sudo pacman -S curl
brew install curl
choco install curl
```