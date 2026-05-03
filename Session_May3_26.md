# 🕸️ WebSockets, LFI, File Upload & API Pentesting  
**Hands‑on Labs from PortSwigger Academy – All in One Place**

> [!NOTE]
> 🔑 **Free Account Required**  
> Sign up at [portswigger.net/web-security](https://portswigger.net/web-security) to access all labs.  
> Each completed lab earns a **Solved** badge – perfect for your learning portfolio.

---

## 📑 Topics (click to jump)

| [WebSocket](#-what-is-websocket) | [HTTP vs WebSocket](#-http-vs-websocket) | [WebSocket Labs](#-websocket-labs) | [LFI Labs](#-local-file-inclusion-lfi-labs) | [File Upload Labs](#-file-upload-labs) | [API Pentesting & Parameter Tampering](#-api-pentesting--parameter-tampering) |
|------------------------------------|------------------------------------------|-------------------------------------|----------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------|

---

## 📘 What is WebSocket?

**WebSocket** is a full‑duplex, persistent communication protocol that allows a client and a server to exchange messages in real time over a single TCP connection.  
It begins as a standard HTTP connection, then upgrades to the WebSocket protocol (`ws://` or `wss://`), after which **both sides can send data independently** – perfect for live chats, gaming, financial tickers, and collaborative editing.

---

### 🔁 HTTP vs WebSocket

| Feature | HTTP (classic) | WebSocket |
|--------|----------------|-----------|
| **Direction** | Half‑duplex (request → response) | Full‑duplex (bidirectional) |
| **Connection** | Short‑lived, stateless | Long‑lived, persistent |
| **Initiator** | Always client | Upgraded from HTTP; both sides can send |
| **Overhead** | High (full HTTP headers each time) | Low (2–10 bytes per frame) |
| **Protocol** | `http://` / `https://` | `ws://` (unencrypted) / `wss://` (encrypted) |
| **Use case** | Documents, REST APIs, form submissions | Real‑time data, live feeds, low‑latency apps |

> ✅ **Why it matters for security testing:** WebSockets often bypass traditional HTTP defences, making them a hidden vector for CSRF‑like hijacking, injection, and unauthorised data exposure.

---

## 🧪 PortSwigger Academy Labs

All labs are **free**, run in isolated environments, and are automatically tracked when you log in.

---

### 🌐 WebSocket Labs

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [Manipulating WebSocket messages to exploit vulnerabilities](https://portswigger.net/web-security/websockets/lab-manipulating-messages-to-exploit-vulnerabilities) | Apprentice |
| 2 | [Manipulating the WebSocket handshake to exploit vulnerabilities](https://portswigger.net/web-security/websockets/lab-manipulating-handshake-to-exploit-vulnerabilities) | Practitioner |
| 3 | [Cross‑site WebSocket hijacking](https://portswigger.net/web-security/websockets/cross-site-websocket-hijacking/lab) | Expert |

📖 **Topic page:** [WebSockets](https://portswigger.net/web-security/websockets)

---

### 📂 Local File Inclusion (LFI) Labs

> 🔥 Classic LFI → wrapper tricks → extension bypass  

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [File inclusion via path traversal](https://portswigger.net/web-security/file-inclusion/lab-file-inclusion-via-path-traversal) | Apprentice |
| 2 | [File inclusion via traversal sequences stripped non‑recursively](https://portswigger.net/web-security/file-inclusion/lab-file-inclusion-via-traversal-sequences-stripped-non-recursively) | Practitioner |
| 3 | [File inclusion via PHP filter wrapper](https://portswigger.net/web-security/file-inclusion/lab-file-inclusion-via-php-filter-wrapper) | Practitioner |
| 4 | [File inclusion via data wrapper](https://portswigger.net/web-security/file-inclusion/lab-file-inclusion-via-data-wrapper) | Practitioner |
| 5 | [File inclusion via wrapper and extension bypass](https://portswigger.net/web-security/file-inclusion/lab-file-inclusion-via-wrapper-and-extension-bypass) | Practitioner |

📖 **Topic page:** [File Inclusion Vulnerabilities](https://portswigger.net/web-security/file-inclusion)

---

### 📤 File Upload Labs

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [Remote code execution via web shell upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload) | Apprentice |
| 2 | [Web shell upload via Content‑Type restriction bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass) | Apprentice |
| 3 | [Web shell upload via path traversal](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal) | Practitioner |
| 4 | [Web shell upload via extension blacklist bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass) | Practitioner |
| 5 | [Web shell upload via obfuscated file extension](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension) | Practitioner |
| 6 | [Remote code execution via polyglot web shell upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload) | Practitioner |
| 7 | [Web shell upload via race condition](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-race-condition) | Expert |

📖 **Topic page:** [File Upload Vulnerabilities](https://portswigger.net/web-security/file-upload)

---

### 🔌 API Pentesting & Parameter Tampering

> 💡 **Parameter tampering** is covered via **mass assignment** and **server‑side parameter pollution** labs – all part of the API testing track.

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [Exploiting an API endpoint using documentation](https://portswigger.net/web-security/api-testing/lab-exploiting-api-endpoint-using-documentation) | Apprentice |
| 2 | [Finding and exploiting an unused API endpoint](https://portswigger.net/web-security/api-testing/lab-exploiting-unused-api-endpoint) | Apprentice |
| 3 | [Exploiting a mass assignment vulnerability](https://portswigger.net/web-security/api-testing/lab-exploiting-mass-assignment-vulnerability) | Practitioner |
| 4 | [Exploiting server‑side parameter pollution in a query string](https://portswigger.net/web-security/api-testing/lab-exploiting-server-side-parameter-pollution-query-string) | Practitioner |
| 5 | [Exploiting server‑side parameter pollution in a REST URL](https://portswigger.net/web-security/api-testing/lab-exploiting-server-side-parameter-pollution-rest-url) | Practitioner |

📖 **Topic page:** [API Testing](https://portswigger.net/web-security/api-testing)

---

## 🛠️ Quick Tips for Students

- Use **Burp Suite Community Edition** [download](https://portswigger.net/burp/communitydownload) or **OWASP ZAP** to intercept and test traffic.
- After each lab, write a short **write‑up** and push it to a public repository to build your portfolio.
- The **Solved** badge motivates – challenge yourself to complete all labs in a track!

---

> 🚀 _Stay curious, keep learning, and happy hacking!_
