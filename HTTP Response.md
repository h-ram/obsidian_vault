#networking 

An **HTTP response** is a message sent by the server back to the client after processing an [[HTTP Request]]. It contains the result of the server's action (whether it’s returning requested content, an error message, or redirecting to another resource). An Example:
```http
HTTP/1.1 200 OK
Content-Type: text/html 
Content-Length: 45 

Welcome to Our website
```
- [[#Response Status Codes]]
---
An HTTP response is composed of 3 main parts:
1. **Response Line**: it contains 3 components:
	1. **HTTP Version**
	2. **Status Code**: A 3-digit code indicating the result of the request
	3. **Status Message**: A short description of the status code (e.g., "OK", "Not Found").
2. **[[HTTP Headers|Reponse Headers]]**: key-value pairs that provide metadata about the message.
3. **Response Body**: The **body** of the response contains the actual data sent from the server to the client. This could be:
	- **HTML content** (for a web page),
	- **JSON or XML** (for API responses),
	- **Binary data** (like images, PDFs, etc.),
	- **Plain text**.
---
### **Response Status Codes**
1. **1xx (Informational)**: Provides information and does not affect the processing of the request.
    - **100 Continue**: The server has received the request headers, and the client should continue with the request body.
2. **2xx (Successful)**: The request was successfully processed.
    - **200 OK**: The request was successful, and the server is returning the requested resource.
    - **201 Created**: The request was successful, and the server has created a new resource.
    - **204 No Content**: The request was successful, but there is no content to return.
3. **3xx (Redirection)**: The client needs to take additional action to complete the request.
    - **301 Moved Permanently**: The resource has permanently moved to a new URL.
    - **302 Found**: The resource is temporarily located at a different URL.
    - **304 Not Modified**: The resource has not been modified since the last request.
4. **4xx (Client Error)**: The client made an error in the request.
    - **400 Bad Request**: The server could not understand the request due to malformed syntax.
    - **401 Unauthorized**: The client is not authorized to access the resource.
    - **403 Forbidden**: The client is not allowed to access the resource.
    - **404 Not Found**: The requested resource could not be found.
5. **5xx (Server Error)**: The server failed to fulfill a valid request.
    - **500 Internal Server Error**: The server encountered an unexpected condition.
    - **502 Bad Gateway**: The server received an invalid response from an upstream server.
    - **503 Service Unavailable**: The server is temporarily unavailable, often due to overload or maintenance.
---