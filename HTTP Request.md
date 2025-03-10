#networking 

An **HTTP request** is a message sent by a client (web browser or API) to a server, asking for a resource or instructing it to perform an action. An example:
```http
GET /index.html HTTP/1.1 
Host: example.com   
User-Agent: Mozilla/5.0 
Accept: text/html
```
- [[#HTTP Request Components]]
- [[#HTTP Methods]]
---
### **HTTP Request Components**
An HTTP Request Has 3 components:
1. **Request Line** : which includes
	1. **Method**: `GET`, `POST`,`PUT`,`PATCH`,`DELETE`..etc
	2. **Path**: to the resources being accesssed (file).
	3. **HTTP Version**: Latest is `HTTP/3` (Jan 2025), Most used is `HTTP/1.1`
```http
	POST /login HTTP/1.1
```
2. **[[HTTP Headers|Request Headers]]** : key-value pairs that provide metadata about the message.
```yaml
	Host: api.example.com
	Content-Type: application/json
	Content-Length: 45
```
3. **Request Body** (optional): The part that carries data. Used usually in POST,PUT,PATCH Requests. The **content-type** header defines the format of the request body.
```json
	{
	  "username": "john_doe",
	  "password": "secure123"
	}
```

```
NOTE: An Empty Line is Mandatory between the Headers and the Body
```
---
### **HTTP Methods**
There are 39 different methods, most common ones are:

| **Method** | **Description**                                                                                                                                                                                                                                                                                                                      |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `GET`      | Requests a specific resource. Additional data can be passed to the server via query strings in the URL (e.g. `?param=value`).                                                                                                                                                                                                        |
| `POST`     | Sends data to the server. It can handle multiple types of input, such as text, PDFs, and other forms of binary data. This data is appended in the request body present after the headers. The POST method is commonly used when sending information (e.g. forms/logins) or uploading data to a website, such as images or documents. |
| `PUT`      | Creates new resources on the server. Allowing this method without proper controls can lead to uploading malicious resources.                                                                                                                                                                                                         |
| `PATCH`    | Applies partial modifications to the resource at the specified location.                                                                                                                                                                                                                                                             |
| `DELETE`   | Deletes an existing resource on the webserver. If not properly secured, can lead to Denial of Service (DoS) by deleting critical files on the web server.                                                                                                                                                                            |
| `HEAD`     | Requests the headers that would be returned if a GET request was made to the server. It doesn't return the request body and is usually made to check the response length before downloading resources.                                                                                                                               |
| `OPTIONS`  | Returns information about the server, such as the methods accepted by it.                                                                                                                                                                                                                                                            |

---
### HTTP Request Examples
```http
POST /login HTTP/1.1
Host: api.example.com
Content-Type: application/json
Content-Length: 45

{
  "username": "john_doe",
  "password": "secure123"
}
```

```http
POST /submit-form HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

name=John+Doe&email=john@example.com
```

```http
POST /upload HTTP/1.1
Host: example.com
Content-Type: multipart/form-data; boundary=----XYZ

------XYZ
Content-Disposition: form-data; name="file"; filename="image.jpg"
Content-Type: image/jpeg

(binary file data)
------XYZ--
```

```http
POST /data HTTP/1.1
Host: example.com
Content-Type: application/xml
Content-Length: 70

<user>
  <name>John Doe</name>
  <email>john@example.com</email>
</user>
```

```http
POST /upload HTTP/1.1
Host: example.com
Content-Type: application/octet-stream
Content-Length: 512000

(binary file data)
```