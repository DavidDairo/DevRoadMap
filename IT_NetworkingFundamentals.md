## ✅ 1. IT & Networking Fundamentals

- [ ] Understand how the internet works (DNS, HTTP, etc.)
- [ ] OSI & TCP/IP models
- [ ] IP addressing, Subnetting, NAT, DHCP
- [ ] Tools: `ping`, `traceroute`, `ipconfig`, `nslookup`, `netstat`
- [ ] Study basic network topology (LAN, WAN, VPN)
- [ ] Resources: CompTIA Network+, NetworkChuck (YouTube), Cisco Packet Tracer





# How the Internet workss?

## Network Basics 

- Local Area Network (LAN) -

- Global Network / World Wide Web (WWW) -


- Fibre optic cables is how internet travels 



## HTTP Basics  (Hyper Text Transfer Protocol)

- Client (Local)  makes request to Server - Server responds  with STATUS CODES.

# 🌐 HTTP Status Codes Cheat Sheet

| Code | Name                        | Description                                              |
|------|-----------------------------|----------------------------------------------------------|
| **1xx – Informational**            |                         |                          |
| 100  | Continue                   | Request received, continue processing                    |
| 101  | Switching Protocols        | Switching to another protocol                            |
| 102  | Processing (WebDAV)        | Server is processing, but no response yet                |

| **2xx – Success**                  |                         |                          |
| 200  | OK                         | Request succeeded                                          |
| 201  | Created                    | Resource created                                           |
| 202  | Accepted                   | Request accepted, processing not complete                 |
| 204  | No Content                 | Success, but no content to return                         |

| **3xx – Redirection**              |                         |                          |
| 301  | Moved Permanently          | Resource moved to a new URL permanently                   |
| 302  | Found (Previously: Moved Temporarily) | Temporary redirect                      |
| 303  | See Other                  | Redirect to another resource using GET                    |
| 304  | Not Modified               | Resource not modified since last request                  |
| 307  | Temporary Redirect         | Temporary redirect, method preserved                      |
| 308  | Permanent Redirect         | Permanent redirect, method preserved                      |

| **4xx – Client Errors**            |                         |                          |
| 400  | Bad Request                | Malformed request syntax                                  |
| 401  | Unauthorized               | Authentication required                                   |
| 403  | Forbidden                  | Server understood request but refuses to authorize        |
| 404  | Not Found                  | Resource not found                                        |
| 405  | Method Not Allowed         | HTTP method not supported for this resource               |
| 408  | Request Timeout            | Client did not send a request in time                     | 
| 409  | Conflict                   | Request conflict with current state of the server         |
| 410  | Gone                       | Resource no longer available                              |
| 415  | Unsupported Media Type     | Media format not supported                                |
| 429  | Too Many Requests          | Rate limiting in effect                                   |

| **5xx – Server Errors**           |                         |                          |
| 500  | Internal Server Error      | Generic server error                                      |
| 501  | Not Implemented            | Server does not support requested functionality           |
| 502  | Bad Gateway                | Invalid response from upstream server                     |
| 503  | Service Unavailable        | Server temporarily unavailable (overloaded or down)       |
| 504  | Gateway Timeout            | Timeout waiting for upstream server                       |
| 505  | HTTP Version Not Supported | Unsupported HTTP version used in request                  |


# 🌐 HTTP Request & Response Structure

Every HTTP message (from client to server or vice versa) has **3 main parts**:

1. **Start Line**
2. **Headers**
3. **Body** (optional)

---

## 📤 HTTP Request Structure

### ✅ 1. Request Start Line
```http
GET /index.html HTTP/1.1

	GET → HTTP method (GET, POST, PUT, DELETE, etc.)
	•	/index.html → URI (resource being requested)
	•	HTTP/1.1 → HTTP version 
```

### ✅ 2. Request Headers
Host: example.com
User-Agent: Mozilla/5.0
Accept: text/html

Headers are key-value pairs that provide **additional information** to the server about the request.

### 📦 Common Request Headers

| Header           | Example Value                         | Description                                              |
|------------------|----------------------------------------|----------------------------------------------------------|
| `Host`           | `example.com`                          | Specifies the domain name of the server                 |
| `User-Agent`     | `Mozilla/5.0 (Windows NT 10.0; Win64)` | Info about the client making the request                |
| `Accept`         | `text/html, application/json`          | Specifies the media types the client can handle         |
| `Accept-Language`| `en-US,en;q=0.9`                       | Preferred languages for the response                    |
| `Content-Type`   | `application/json`                     | Format of the request body (e.g. JSON, form data)       |
| `Authorization`  | `Bearer eyJhbGci...`                   | Sends authentication credentials (e.g. API tokens)      |
| `Referer`        | `https://example.com/form`             | URL of the page making the request                      |
| `Connection`     | `keep-alive`                           | Controls whether the connection stays open              |
| `Cookie`         | `sessionid=abc123`                     | Sends stored cookies to the server                      |
| `Content-Length` | `123`                                  | Size of the request body in bytes                       |

---

### 📝 Example

```http
POST /login HTTP/1.1
Host: example.com
User-Agent: CustomApp/1.0
Accept: application/json
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1...
Content-Length: 58
```


## ✅ 3. Request Body (Optional)

The **request body** is used to send data from the client to the server — especially with methods like `POST`, `PUT`, or `PATCH`.

It usually contains **structured data** such as JSON, XML, or form-encoded data.

---

### 📦 Common Use Cases

| HTTP Method | Use Case                        | Body Required? |
|-------------|----------------------------------|----------------|
| `GET`       | Retrieve data                    | ❌ No           |
| `POST`      | Create a new resource            | ✅ Yes          |
| `PUT`       | Replace a resource               | ✅ Yes          |
| `PATCH`     | Partially update a resource      | ✅ Yes          |
| `DELETE`    | Delete a resource (body optional)| ⚠️ Optional     |

---

### 📄 Content Types for Request Body

| Content-Type               | Format Example                      |
|----------------------------|-------------------------------------|
| `application/json`         | `{ "name": "Blackistan" }`          |
| `application/x-www-form-urlencoded` | `name=Blackistan&email=test@example.com` |
| `multipart/form-data`      | Used for file uploads               |
| `text/plain`               | Plain text                         |

---

### 📝 JSON Body Example

```http
POST /api/users HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "username": "blackistan",
  "email": "blacki@example.com",
  "password": "strongpass123"
}
```


## 📤 HTTP Response Structure

The **HTTP response** is what the server sends back to the client after processing the request. Like the request, it has 3 main parts:

1. **Status Line**
2. **Headers**
3. **Body** (optional)

---

### ✅ 1. Response Status Line

```http
HTTP/1.1 200 OK
```

## ✅ 2. HTTP Response Headers

**Response headers** are key-value pairs sent by the server to provide **metadata about the response**. These help the client understand how to handle the returned data.

---

### 📦 Common Response Headers

| Header             | Example Value                            | Description                                                         |
|--------------------|-------------------------------------------|---------------------------------------------------------------------|
| `Content-Type`     | `application/json`                        | Format of the response body (e.g. JSON, HTML, plain text)           |
| `Content-Length`   | `1234`                                    | Size of the response body in bytes                                  |
| `Location`         | `/api/users/42`                           | Used with `201 Created` to indicate the URL of the new resource     |
| `Set-Cookie`       | `sessionid=abc123; HttpOnly`              | Sets a cookie on the client side                                    |
| `Cache-Control`    | `no-cache` / `max-age=3600`               | Defines caching behavior for the client or proxy                    |
| `ETag`             | `"abc123etagvalue"`                       | Unique identifier for a version of a resource (used for caching)    |
| `Expires`          | `Wed, 21 Oct 2025 07:28:00 GMT`           | Tells when the response content should be considered "stale"        |
| `Access-Control-Allow-Origin` | `*`                            | CORS header – controls which domains can access the resource        |
| `WWW-Authenticate` | `Bearer realm="Access to the API"`        | Indicates required authentication scheme (e.g., Basic, Bearer)      |
| `Retry-After`      | `120`                                     | Tells client how long to wait before retrying (used with `503`)     |
| `Server`           | `nginx/1.18.0`                            | Info about the server software (can be hidden for security reasons) |

---

### 📝 Example Response Header Block

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 256
Cache-Control: no-cache
Set-Cookie: sessionid=xyz123; HttpOnly
Access-Control-Allow-Origin: *
```

## ✅ HTTP Response Body

The **response body** is the actual content returned by the server after processing the request.

- It's **optional** (some responses like `204 No Content` don’t include a body).
- The format is usually defined by the `Content-Type` header.
- It can contain data (like JSON or HTML), error messages, or files.

---

### 📦 Common Body Content Formats

| Content-Type               | Format Description                     |
|----------------------------|-----------------------------------------|
| `application/json`         | JSON (JavaScript Object Notation)       |
| `text/html`                | HTML web pages                          |
| `text/plain`               | Plain text                              |
| `application/xml`          | XML data                                |
| `application/octet-stream`| Binary data (e.g., files)               |
| `image/jpeg`, `image/png`  | Image files                             |

---

### 📝 Example JSON Body (for a `201 Created` Response)

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": 42,
  "username": "blackistan",
  "email": "blacki@example.com",
  "created_at": "2025-04-15T12:00:00Z"
}
```

### ⚠️ Body Not Always Present

Not all HTTP responses include a body — some status codes intentionally return **no content**.

---

#### 📭 Status Codes Without a Response Body

| Status Code | Name                 | Has Body? | Description                                         |
|-------------|----------------------|-----------|-----------------------------------------------------|
| `204`       | No Content           | ❌ No      | The request was successful, but there's nothing to return. |
| `304`       | Not Modified         | ❌ No      | Resource has not changed since the last request. Used with caching. |
| `100`       | Continue             | ❌ No      | Temporary status to indicate the request should continue. |
| `101`       | Switching Protocols  | ❌ No      | Server is switching to a different protocol.        |

---

#### ✅ Other Codes That *May* or *Often* Include a Body

| Status Code | Name                    | Has Body? | Description                                          |
|-------------|-------------------------|-----------|------------------------------------------------------|
| `200`       | OK                      | ✅ Yes     | Standard success response with content.              |
| `201`       | Created                 | ✅ Yes     | Includes the newly created resource in the body.     |
| `400`       | Bad Request             | ✅ Yes     | Often includes error messages and validation details.|
| `401`       | Unauthorized            | ✅ Yes     | May contain instructions or messages.                |
| `404`       | Not Found               | ✅ Yes     | Usually includes a message like "Page Not Found."    |
| `500`       | Internal Server Error   | ✅ Yes     | May include diagnostic info or stack trace (not in production). |

---

> 💡 Tip: Even if a response **can** include a body, it’s not always required. The presence of a body depends on the **API or server implementation**.


## HTTP Overview

1.  HTTP 1.0 is **STATELESS** - **Stateless** means that the **server does NOT remember anything** about previous requests made by the same client. 
    Every request is treated as if it's **brand new**, with **no memory of past interactions**.

2. Based on TCP/IP - ## 🧱 The TCP/IP Model (4 Layers)

HTTP runs on top of the **TCP/IP networking model**, which has 4 layers:

| Layer             | Example Protocols              | Role                                         |
|------------------|--------------------------------|----------------------------------------------|
| **Application**   | HTTP, FTP, SMTP, DNS           | What the user interacts with (web, email)    |
| **Transport**     | TCP, UDP                       | Reliable or fast delivery of data            |
| **Internet**      | IP                             | Routing data across networks (IP addresses)  |
| **Network Access**| Ethernet, Wi-Fi, ARP           | Physical delivery over cables/wireless       |


## 🌐 HTTP/1.0 Lives at the Application Layer

- **HTTP** is an **Application Layer** protocol.
- It **relies on TCP** (Transport Layer) to deliver data **reliably** between client and server.


3. 3 parts to the request/respsonse message - 

1. **Start Line** – Describes the request or response status  
   → `GET /home HTTP/1.1` or `HTTP/1.1 200 OK`

2. **Headers** – Metadata (e.g. content type, cookies, auth)  
   → `Content-Type: application/json`

3. **Body** – Optional data (like form inputs or JSON)  
   → `{ "username": "blackistan" }`