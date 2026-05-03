# 🛡️ Burp Suite Academy – Web Security Lab Catalogue  
*All the hands‑on labs you need to master XSS, SSRF, CSRF, Path Traversal, File Upload, and API Testing – completely free and ready to hack.*

> [!NOTE]
> **🔑 FREE ACCOUNT REQUIRED**  
> Students must register at [portswigger.net/web-security](https://portswigger.net/web-security) to access the labs.  
> Progress is automatically tracked and each completed lab earns a **Solved** badge.

---

## 📑 Quick‑Jump Index

| [XSS](#-cross‑site-scripting-xss) | [SSRF](#-server‑side-request-forgery-ssrf) | [CSRF](#-cross‑site-request-forgery-csrf) | [Path Traversal](#-path-traversal) | [File Upload](#-file-upload-vulnerabilities) | [API Testing](#-api-testing) | [Burp Suite](#-what-is-burp-suite) | [ZAP](#-what-is-owasp-zap) |
|--------------------------------------|---------------------------------------------|--------------------------------------------|------------------------------------|----------------------------------------------|------------------------------|--------------------------------------|-----------------------------|

---

## ⚔️ Vulnerability Learning Paths

### 🔥 Cross‑Site Scripting (XSS)
*Reflected, Stored, DOM‑based, AngularJS, CSP bypass – the full spectrum of XSS.*

> **📚 Main Topic Page**  
> 🔗 [https://portswigger.net/web-security/cross-site-scripting](https://portswigger.net/web-security/cross-site-scripting)

#### 🧪 Individual Labs (30 total)

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded) | Apprentice |
| 2 | [Stored XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded) | Apprentice |
| 3 | [DOM XSS in `document.write` sink using source `location.search`](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink) | Apprentice |
| 4 | [DOM XSS in `innerHTML` sink using source `location.search`](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink) | Apprentice |
| 5 | [DOM XSS in jQuery anchor `href` attribute sink using `location.search` source](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink) | Apprentice |
| 6 | [DOM XSS in jQuery selector sink using a hashchange event](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hashchange-event) | Apprentice |
| 7 | [Reflected XSS into attribute with angle brackets HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-attribute-angle-brackets-html-encoded) | Apprentice |
| 8 | [Stored XSS into anchor `href` attribute with double quotes HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-anchor-href-attribute-double-quotes-html-encoded) | Apprentice |
| 9 | [Reflected XSS into a JavaScript string with angle brackets HTML encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-javascript-string-angle-brackets-html-encoded) | Apprentice |
| 10 | [DOM XSS in `document.write` sink using source `location.search` inside a select element](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink-inside-select-element) | Apprentice |
| 11 | [DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-angularjs-expression) | Practitioner |
| 12 | [Reflected DOM XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-reflected-dom-xss) | Practitioner |
| 13 | [Stored DOM XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-stored-dom-xss) | Practitioner |
| 14 | [Reflected XSS protected by CSP, with CSP bypass](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-csp-bypass) | Practitioner |
| 15 | [Reflected XSS into HTML context with most tags and attributes blocked](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-most-tags-attributes-blocked) | Practitioner |
| 16 | [Reflected XSS into HTML context with all tags blocked except custom ones](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-all-tags-blocked-except-custom-ones) | Practitioner |
| 17 | [Reflected XSS with some SVG markup allowed](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-svg-markup-allowed) | Practitioner |
| 18 | [Reflected XSS with event handlers and `href` attributes blocked](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-event-handlers-href-attributes-blocked) | Practitioner |
| 19 | [Reflected XSS in canonical link tag](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-canonical-link-tag) | Practitioner |
| 20 | [Reflected XSS into a JavaScript string with single quote and backslash escaped](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-javascript-string-single-quote-backslash-escaped) | Practitioner |
| 21 | [Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-template-literal) | Practitioner |
| 22 | [Exploiting XSS to bypass CSRF defenses](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-bypass-csrf-defenses) | Practitioner |
| 23 | [Exploiting cross-site scripting to steal cookies](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-steal-cookies) | Practitioner |
| 24 | [Exploiting cross-site scripting to capture passwords](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-capture-passwords) | Practitioner |
| 25 | [Exploiting XSS to perform CSRF](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-perform-csrf) | Practitioner |
| 26 | [Reflected XSS protected by very strict CSP, with dangling markup attack](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-very-strict-csp-dangling-markup) | Expert |
| 27 | [Reflected XSS protected by CSP, with CSP bypass](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-csp-bypass) | Expert |
| 28 | [Exploiting clickjacking vulnerability to trigger DOM-based XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-clickjacking) | Expert |
| 29 | [DOM XSS using web messages and `JSON.parse`](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-web-messages-json-parse) | Practitioner |
| 30 | [DOM XSS using web messages](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-web-messages) | Practitioner |

---

### 🌐 Server‑Side Request Forgery (SSRF)
*Egressed, blind, internal service probing, cloud metadata exfiltration.*

> **📚 Main Topic Page**  
> 🔗 [https://portswigger.net/web-security/ssrf](https://portswigger.net/web-security/ssrf)

#### 🧪 Individual Labs

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [Basic SSRF against the local server](https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-localhost) | Apprentice |
| 2 | [Basic SSRF against another back-end system](https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-backend-system) | Apprentice |
| 3 | [SSRF with blacklist-based input filter](https://portswigger.net/web-security/ssrf/lab-ssrf-with-blacklist-filter) | Practitioner |
| 4 | [SSRF with whitelist-based input filter](https://portswigger.net/web-security/ssrf/lab-ssrf-with-whitelist-filter) | Practitioner |
| 5 | [SSRF with filter bypass via open redirection vulnerability](https://portswigger.net/web-security/ssrf/lab-ssrf-filter-bypass-via-open-redirection) | Practitioner |
| 6 | [Blind SSRF with out-of-band detection](https://portswigger.net/web-security/ssrf/lab-blind-ssrf-out-of-band-detection) | Practitioner |
| 7 | [Blind SSRF with Shellshock exploitation](https://portswigger.net/web-security/ssrf/lab-blind-ssrf-shellshock-exploitation) | Expert |
| 8 | [SSRF via flawed request parsing](https://portswigger.net/web-security/ssrf/lab-ssrf-via-flawed-request-parsing) | Expert |
| 9 | [Host validation bypass via connection state attack](https://portswigger.net/web-security/ssrf/lab-host-validation-bypass-via-connection-state-attack) | Expert |
| 10 | [Routing-based SSRF](https://portswigger.net/web-security/ssrf/lab-routing-based-ssrf) | Expert |

---

### 🛡️ Cross‑Site Request Forgery (CSRF)
*Token validation, SameSite cookie tricks, and elective bypass techniques.*

> **📚 Main Topic Page**  
> 🔗 [https://portswigger.net/web-security/csrf](https://portswigger.net/web-security/csrf)

#### 🧪 Individual Labs

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [CSRF vulnerability with no defenses](https://portswigger.net/web-security/csrf/lab-no-defenses) | Apprentice |
| 2 | [CSRF where token validation depends on request method](https://portswigger.net/web-security/csrf/lab-token-validation-depends-on-request-method) | Apprentice |
| 3 | [CSRF where token validation depends on token being present](https://portswigger.net/web-security/csrf/lab-token-validation-depends-on-token-being-present) | Apprentice |
| 4 | [CSRF where token is not tied to user session](https://portswigger.net/web-security/csrf/lab-token-not-tied-to-user-session) | Practitioner |
| 5 | [CSRF where token is tied to non-session cookie](https://portswigger.net/web-security/csrf/lab-token-tied-to-non-session-cookie) | Practitioner |
| 6 | [CSRF where token is duplicated in cookie](https://portswigger.net/web-security/csrf/lab-token-duplicated-in-cookie) | Practitioner |
| 7 | [CSRF where Referer validation depends on header being present](https://portswigger.net/web-security/csrf/lab-referer-validation-depends-on-header-being-present) | Practitioner |
| 8 | [CSRF with broken Referer validation](https://portswigger.net/web-security/csrf/lab-broken-referer-validation) | Practitioner |
| 9 | [SameSite Lax bypass via method override](https://portswigger.net/web-security/csrf/lab-samesite-lax-bypass-via-method-override) | Practitioner |
| 10 | [SameSite Strict bypass via client-side redirect](https://portswigger.net/web-security/csrf/lab-samesite-strict-bypass-via-client-side-redirect) | Practitioner |
| 11 | [SameSite Strict bypass via sibling domain](https://portswigger.net/web-security/csrf/lab-samesite-strict-bypass-via-sibling-domain) | Practitioner |
| 12 | [Performing CSRF exploits over GraphQL](https://portswigger.net/web-security/csrf/lab-performing-csrf-exploits-over-graphql) | Practitioner |

> 💡 *The official CSRF learning path can be found here:*  
> 🔗 [https://portswigger.net/web-security/csrf/learning-path](https://portswigger.net/web-security/csrf/learning-path)

---

### 📁 Path Traversal
*Directory climbing, encoding evasions, null‑byte injection, and more.*

> **📚 Main Topic Page**  
> 🔗 [https://portswigger.net/web-security/file-path-traversal](https://portswigger.net/web-security/file-path-traversal)

#### 🧪 Individual Labs

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [File path traversal, simple case](https://portswigger.net/web-security/file-path-traversal/lab-simple) | Apprentice |
| 2 | [File path traversal, traversal sequences blocked with absolute path bypass](https://portswigger.net/web-security/file-path-traversal/lab-absolute-path-bypass) | Practitioner |
| 3 | [File path traversal, traversal sequences stripped non-recursively](https://portswigger.net/web-security/file-path-traversal/lab-traversal-sequences-stripped-non-recursively) | Practitioner |
| 4 | [File path traversal, traversal sequences stripped with superfluous URL-decode](https://portswigger.net/web-security/file-path-traversal/lab-superfluous-url-decode) | Practitioner |
| 5 | [File path traversal, validation of start of path](https://portswigger.net/web-security/file-path-traversal/lab-validation-of-start-of-path) | Practitioner |
| 6 | [File path traversal, validation of file extension with null byte bypass](https://portswigger.net/web-security/file-path-traversal/lab-extension-null-byte-bypass) | Practitioner |
| 7 | [Web shell upload via path traversal](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal) | Practitioner |

---

### 📤 File Upload Vulnerabilities
*Unrestricted uploads, client‑/server‑side filters, polyglot files, RCE via upload.*

> **📚 Main Topic Page**  
> 🔗 [https://portswigger.net/web-security/file-upload](https://portswigger.net/web-security/file-upload)

#### 🧪 Individual Labs

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [Remote code execution via web shell upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload) | Apprentice |
| 2 | [Web shell upload via Content-Type restriction bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass) | Apprentice |
| 3 | [Web shell upload via path traversal](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal) | Practitioner |
| 4 | [Web shell upload via extension blacklist bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass) | Practitioner |
| 5 | [Web shell upload via obfuscated file extension](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension) | Practitioner |
| 6 | [Remote code execution via polyglot web shell upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload) | Practitioner |
| 7 | [Web shell upload via race condition](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-race-condition) | Expert |

---

### 🔌 API Testing
*REST & GraphQL attacks, mass assignment, injection, schema discovery.*

> **📚 Main Topic Page**  
> 🔗 [https://portswigger.net/web-security/api-testing](https://portswigger.net/web-security/api-testing)

#### 🧪 Individual Labs

| # | Lab Name | Level |
|---|----------|-------|
| 1 | [Exploiting an API endpoint using documentation](https://portswigger.net/web-security/api-testing/lab-exploiting-api-endpoint-using-documentation) | Apprentice |
| 2 | [Finding and exploiting an unused API endpoint](https://portswigger.net/web-security/api-testing/lab-exploiting-unused-api-endpoint) | Apprentice |
| 3 | [Exploiting a mass assignment vulnerability](https://portswigger.net/web-security/api-testing/lab-exploiting-mass-assignment-vulnerability) | Practitioner |
| 4 | [Exploiting server-side parameter pollution in a query string](https://portswigger.net/web-security/api-testing/lab-exploiting-server-side-parameter-pollution-query-string) | Practitioner |
| 5 | [Exploiting server-side parameter pollution in a REST URL](https://portswigger.net/web-security/api-testing/lab-exploiting-server-side-parameter-pollution-rest-url) | Practitioner |

---

## 🛠️ What is Burp Suite?

Burp Suite is a powerful Java-based framework for web application security testing, created by **PortSwigger**. It’s used by security professionals and bug bounty hunters worldwide to intercept, inspect, and modify HTTP traffic between the browser and the target server. Burp Suite includes:

- **Proxy** – Intercept and modify HTTP/S requests in real time  
- **Repeater** – Resend and test different payloads on individual requests  
- **Intruder** – Automate attacks like fuzzing and brute‑forcing  
- **Scanner** – Automatically scan for vulnerabilities (Professional edition)  
- **Decoder, Comparer, Sequencer, Collaborator** – And many more utilities  

> **Download Burp Suite:** [https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload)

---

## 📝 How to Set Up Burp Suite Proxy – Step by Step

### Step 1: Download & Install
1. Go to [https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload) and download the latest Community Edition.
2. Install and launch Burp Suite. When asked to select a project file, just click **Next** and **Start Burp**.

### Step 2: Intercept Traffic with Burp Proxy
1. Go to the **Proxy > Intercept** tab.
2. Set the **intercept toggle** to **Intercept on**.
3. Click **Open Browser**. This launches Burp's pre‑configured Chromium browser.

> 💡 *Burp's browser is already configured to work with Burp – no extra setup needed!*

### Step 3: Forward & View Requests
1. In Burp's browser, try visiting a website like `https://portswigger.net`.
2. The browser will hang – Burp has intercepted the request!
3. On the **Proxy > Intercept** tab, click **Forward** to send the request.
4. Click **Forward** again as needed until the page loads.
5. Switch the intercept toggle to **Intercept off** to browse without interruption.

### Step 4: View HTTP History
- Go to **Proxy > HTTP history** to see all requests and responses that passed through Burp Proxy.
- Click any entry to view the raw HTTP request and response.

### Step 5 (Optional): Set Up an External Browser
If you want to use your own browser (e.g., Firefox) instead of Burp's browser:

1. Configure your browser’s proxy settings:
   - **Firefox:** Settings → Network Settings → Manual proxy configuration. Set HTTP Proxy to `127.0.0.1`, port `8080`, and check “Also use this proxy for HTTPS”.
   - **Chrome:** Settings → System → Open your computer’s proxy settings → configure Web Proxy (HTTP) to `127.0.0.1:8080`.
2. Install Burp’s CA certificate to inspect HTTPS traffic:
   - In Burp, go to **Proxy > Options > Proxy Listeners**. Click **Import/Export CA certificate** → Export certificate in DER format.
   - Import the certificate into your browser’s Trusted Root Certification Authorities.
3. Test: visit any HTTPS site; you should see traffic in Burp’s HTTP history.

> 📚 **Official guide:** [https://portswigger.net/burp/documentation/desktop/getting-started/proxy-setup](https://portswigger.net/burp/documentation/desktop/getting-started/proxy-setup)

---

## 🛡️ What is OWASP ZAP?

**OWASP ZAP (Zed Attack Proxy)** is a free, open‑source web application security scanner – an excellent alternative to Burp Suite. It’s maintained by the OWASP community and provides:

- **Intercepting Proxy** – View and modify HTTP/S traffic in real time  
- **Active & Passive Scanner** – Automatically find vulnerabilities  
- **Fuzzer, Scripts, WebSocket support, and more**  
- **Automated scanning** for CI/CD pipelines  

> **Download OWASP ZAP:** [https://www.zaproxy.org/download/](https://www.zaproxy.org/download/)

---

## 📝 How to Set Up OWASP ZAP Proxy – Step by Step

### Step 1: Download & Install
1. Visit [https://www.zaproxy.org/download/](https://www.zaproxy.org/download/) and download the version for your operating system.
2. Install and launch ZAP.

### Step 2: Configure the Local Proxy Listener
1. By default, ZAP listens on `localhost:8080`. You can verify this at **Tools > Options > Local Proxies**.
2. The default address (`localhost`) and port (`8080`) work for most setups.

### Step 3: Configure Your Browser
1. Set your browser’s proxy to `127.0.0.1:8080` (same as Burp Suite).
   - **Firefox:** Settings → Network Settings → Manual proxy configuration → HTTP Proxy: `127.0.0.1`, Port: `8080`. Enable “Also use this proxy for HTTPS”.
   - **Chrome:** Settings → System → Open your computer’s proxy settings → configure `127.0.0.1:8080`.
2. **FoxyProxy (recommended):** Install the FoxyProxy browser extension and create a proxy entry for `127.0.0.1:8080`.

### Step 4: Install ZAP’s CA Certificate (for HTTPS)
1. In ZAP, go to **Tools > Options > Network > Server Certificates**.
2. Click **Generate** to create a new root CA certificate for ZAP.
3. Click **Save** to export the certificate file (`.cer` or `.der`).
4. Import the certificate into your browser’s Trusted Root Certification Authorities.

### Step 5: Start Testing
1. Open any website in your configured browser.
2. You should see the traffic in ZAP’s **Sites** tree and the **History** tab.
3. Right‑click any request and choose **Attack > Active Scan** to automatically test for vulnerabilities.

> 📚 **Official guide:** [https://www.zaproxy.org/docs/desktop/start/proxies/](https://www.zaproxy.org/docs/desktop/start/proxies/)

---

## 👨‍🏫 Instructor Tips

| 💡 Tip | 💬 Details |
|--------|------------|
| **Classroom tracking** | Use the Academy’s *My Account* panel to see who has solved which lab. |
| **Tooling** | Pair with [Burp Suite Community Edition](https://portswigger.net/burp/communitydownload) or [OWASP ZAP](https://www.zaproxy.org/) for realistic request manipulation. |
| **Portfolio building** | Encourage students to push write‑ups to a public GitHub repo – great for job hunting! |
| **Motivation** | Celebrate each *Solved* badge; little wins keep engagement high. |
| **Environment safety** | All labs run in safe, disposable environments – no legal worries. |

---

> 🚀 *Stay curious, break things ethically, and happy learning!*
