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



### 📌 What is an IP Address
- An IP address (short for Internet Protocol address) is a unique string of numbers (and sometimes letters) assigned to each device connected to a network—like your phone, laptop, or server. It works like a home address for your device, so it can send and receive data on the internet.

# 🔍 Types of IP Addresses

## ✅ IPv4 (Internet Protocol version 4)
- Introduced: 1980s
- Format: `xxx.xxx.xxx.xxx` (four numbers, each 0–255)
- Example: `192.168.0.1`
- Total addresses: ~4.3 billion
- Address size: **32-bit**

---

## ✅ IPv6 (Internet Protocol version 6)
- Introduced: 1998 (to replace IPv4)
- Format: `xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx` (hexadecimal)
- Example: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
- Total addresses: **340 undecillion**
- Address size: **128-bit**

---

## 🔍 Key Differences

| Feature                    | IPv4                          | IPv6                                      |
|----------------------------|-------------------------------|--------------------------------------------|
| **Address Size**           | 32-bit                        | 128-bit                                    |
| **Address Format**         | Decimal (e.g. `192.168.1.1`)  | Hexadecimal (e.g. `2001:0db8::1`)          |
| **Total IP Addresses**     | ~4.3 billion                  | 340 undecillion                            |
| **Header Complexity**      | Simple                        | More complex                               |
| **Security**               | Optional (IPsec)              | Built-in IPsec                             |
| **NAT Required?**          | Yes                           | No (enough IPs for all devices)            |
| **Speed**                  | Fast                          | Often faster for modern routing            |

---

## 🧠 Analogy

> IPv4 is like a phonebook that’s run out of numbers. IPv6 is like inventing a whole new planet with infinite numbers.

---

## 🔚 Summary

- IPv4 is still widely used but running out of space.
- IPv6 is the future: faster, more secure, and has *way* more addresses.

## 📦 IPv4 Format Breakdown

### Structure:
IPv4 is written as **four decimal numbers** separated by dots: `192.168.1.1`

Each number is called an **octet**, and it represents **8 bits**.  
So the full IP address is **32 bits total** (4 × 8 bits).

---

### Example: `192.168.1.1`

| Octet     | Binary (8 bits)      | Meaning                                       |
|-----------|----------------------|-----------------------------------------------|
| `192`     | `11000000`           | Network part                                  |
| `168`     | `10101000`           | Network/Subnet part                           |
| `1`       | `00000001`           | Host (device) part                            |
| `1`       | `00000001`           | Host (device) part                            |

---

## 🏠 Network vs Host

IPv4 is often divided into **network** and **host** parts:

- **Network**: Identifies the network or subnet
- **Host**: Identifies a device within that network

The division depends on the **subnet mask**.

---

## 🧪 Example with Subnet Mask

If the subnet mask is `255.255.255.0`, then:

- First **3 octets** = Network (`192.168.1`)
- Last **octet** = Host (`.1` → device on that network)

So, `192.168.1.1` means:
> Device 1 on network `192.168.1.0`

---

## ⚠️ Each Octet's Value

Each octet can range from `0` to `255` because:
- It holds **8 bits**
- `2^8 = 256` values (0–255)

---

## 🧠 Analogy

> Think of an IP like a street address:  
> - **Network** = Street name  
> - **Host** = House number

So `192.168.1.1` is like saying:
> "House 1 on Street 192.168.1"

---

## ✅ Summary

- IPv4 = 4 numbers (octets) separated by dots
- Each octet = 8 bits = values from 0–255
- Subnet mask determines how it's split between **network** and **host**
- Format helps routers and devices know **where data should go**

# 🧠 Breakdown of IP Address Format

- **IPv4** – Most common (e.g. `192.168.1.1`)
- **IPv6** – Newer, longer format (e.g. `2001:0db8::1`)


# 🧮 What is a Subnet Mask?

A **subnet mask** is a 32-bit number that works **alongside an IP address** to separate the **network** part from the **host** part of that address.

It helps devices know:
- Which part of the IP address refers to the **network**
- Which part refers to the **specific device (host)** on that network

---

## 📦 Example

### IP Address: 192.168.1.10
### Subnet Mask: 255.255.255.0

### Meaning:
- First **24 bits** = Network part → `192.168.1`
- Last **8 bits** = Host part → `10` (device number)

So this tells us:
> Device 10 on network `192.168.1.0`

---

## 🔍 Common Subnet Masks (IPv4)

| Subnet Mask       | CIDR Notation | Number of Hosts | Notes                         |
|-------------------|----------------|------------------|-------------------------------|
| `255.0.0.0`       | `/8`           | 16 million+      | Class A (large networks)      |
| `255.255.0.0`     | `/16`          | 65,534           | Class B                       |
| `255.255.255.0`   | `/24`          | 254              | Class C (common for LANs)     |
| `255.255.255.192` | `/26`          | 62               | Small subnets                 |

---

## 📘 CIDR Notation

Instead of writing the full subnet mask, you can use **CIDR (Classless Inter-Domain Routing)** notation: `192.168.1.0/24`

- `/24` means the **first 24 bits** are the network part
- Equivalent to `255.255.255.0`

---

## 🧠 Why Subnet Masks Matter

- Helps devices **know who’s local and who’s remote**
- Routers use it to **route traffic efficiently**
- Allows **subnetting**: dividing one large network into smaller ones

---

## 🧠 Analogy

> If an IP address is a **phone number**, then a subnet mask is the **area code system** — it tells you which numbers belong to your local area and which are long-distance.

---

## ✅ Summary

- A **subnet mask** defines how much of an IP address is for the **network** vs the **device (host)**
- It improves routing, organization, and security in a network
- Common subnet: `255.255.255.0` = `/24`





# 🌐 What is a Domain?

A **domain** is the human-friendly address used to access websites on the internet.

Instead of typing an IP address like `172.217.14.206`, you type something like: `www.google.com`

---

## 📌 Parts of a Domain Name

Example: `www.google.com`

| Part             | Description                                  |
|------------------|----------------------------------------------|
| **www**          | Subdomain (optional)                         |
| **google**      | Second-level domain (chosen by the user)     |
| **.com**         | Top-level domain (TLD, like `.com`, `.org`)  |

---

## 🧠 How It Works

1. You type a domain like `www.example.com` into your browser.
2. The browser asks a **DNS (Domain Name System)** server to translate it into an **IP address**.
3. That IP address points to the server where the website lives.
4. You get connected and see the site.

---

## 💡 Fun Fact

- Domains are **rented**, not owned. You buy them from registrars like GoDaddy or Namecheap.
- Domains are essential for branding, SEO, and web identity.

---

## ✅ Common TLDs (Top-Level Domains)

| TLD      | Meaning                     |
|----------|-----------------------------|
| `.com`   | Commercial (most common)    |
| `.org`   | Organizations               |
| `.net`   | Networks                    |
| `.edu`   | Educational institutions    |
| `.gov`   | Government websites         |

---
## 🌍 Difference Between TLD, ccTLD, and gTLD (with Examples)

| Type      | Full Form                     | Description                                                                 | Example Domains                  |
|-----------|-------------------------------|-----------------------------------------------------------------------------|----------------------------------|
| **TLD**   | Top-Level Domain               | The highest level in the domain name system hierarchy.                      | `.com`, `.org`, `.net`, `.uk`    |
| **ccTLD** | Country Code Top-Level Domain  | TLDs reserved for countries or territories. Two-letter codes.              | `.uk` (UK), `.fr` (France), `.jp` (Japan), `.ng` (Nigeria) |
| **gTLD**  | Generic Top-Level Domain       | TLDs not tied to geography. Used by businesses, orgs, communities, etc.    | `.com`, `.org`, `.xyz`, `.online`, `.tech`, `.store`       |
## 🧠 Analogy

> A **domain** is like a **storefront name**, and the **IP address** is like the **physical location**. DNS is the **directory** that matches them up.

# 🌐 What is a Domain Name Server (DNS)?

A **Domain Name Server (DNS)** is like the **internet’s phonebook**.

It translates **human-readable domain names** (like `www.google.com`) into **IP addresses** (like `142.250.72.14`) that computers use to identify each other.

---

## 🧠 Why DNS is Important

- Computers use IP addresses to communicate.
- People prefer names (like `example.com`) over numbers.
- DNS makes it easier to browse the web without memorizing IPs.

---

## ⚙️ How DNS Works (Step-by-Step)

1. **You type a website** into your browser (e.g. `www.example.com`).
2. Your computer asks the **DNS server** to find the **IP address** of that domain.
3. The DNS server responds with the correct IP (e.g. `93.184.216.34`).
4. Your browser uses that IP to connect to the website’s server.
5. The website loads!

---

## 📌 Types of DNS Servers

| Type                 | Description                                                   |
|----------------------|---------------------------------------------------------------|
| **DNS Resolver**     | The first stop; checks cache or queries other servers         |
| **Root Name Server** | Knows where to find top-level domains (like `.com`, `.org`)   |
| **TLD Server**       | Directs the query to the server for a specific TLD (e.g. `.com`)|
| **Authoritative DNS**| Has the final answer – gives the actual IP address            |

---

## 🧠 Analogy

> DNS is like asking a librarian (DNS Resolver) where to find a book (IP address) for a website (domain name). The librarian checks a series of shelves (DNS servers) until they find the right one.

---

## 💡 Bonus

- DNS issues can make websites **fail to load**, even if your internet is fine.
- You can use custom DNS like **Google DNS** (`8.8.8.8`) or **Cloudflare DNS** (`1.1.1.1`) for speed & privacy.