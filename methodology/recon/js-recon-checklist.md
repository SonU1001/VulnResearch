# 📜 JavaScript Recon Checklist

> Extract hidden endpoints, secrets, and logic flaws from client-side JavaScript

---

# 🎯 Objective

Identify hidden API endpoints, sensitive data, and attack vectors from JavaScript files.

---

# 🔍 1. Locate JavaScript Files

## Sources

* View page source
* Browser DevTools → Network tab
* Burp Suite

---

## Look For

```plaintext
/main.js
/app.js
/bundle.js
/static/js/
```

---

# 🧠 2. Extract Endpoints

## Search Keywords

```plaintext
/api/
/v1/
/auth/
/login
```

---

## Example

```javascript
fetch("/api/user/data")
axios.get("/api/admin")
```

👉 These are hidden endpoints

---

# 🔐 3. Look for Secrets

## Keywords

```plaintext
api_key
token
secret
authorization
```

---

## Example

```javascript
const API_KEY = "abcd1234";
```

👉 Critical finding

---

# 🔁 4. Identify Parameters

## Look For

```javascript
id:
user_id:
email:
role:
```

---

👉 These can lead to:

* IDOR
* privilege escalation

---

# ⚡ 5. Analyze Logic

## Check

* Role checks
* Hidden conditions
* Feature flags

---

## Example

```javascript
if(user.role === "admin")
```

👉 Try manipulating role

---

# 📡 6. DOM XSS Sources & Sinks

## Sources

```javascript
location.search
document.URL
document.referrer
```

---

## Sinks

```javascript
innerHTML
document.write
eval()
```

---

👉 Source → Sink = XSS

---

# 🔍 7. Hidden Functionality

## Look For

```javascript
/admin/
/debug/
/internal/
```

---

👉 Often not visible in UI

---

# 🧪 8. Beautify & Analyze Code

## Tools

* JS Beautifier
* Browser DevTools

---

👉 Makes code readable

---

# 🌐 9. Third-Party Scripts

## Check

* External JS files
* CDN scripts

---

👉 May expose keys or weak integrations

---

# 🔁 10. Dynamic Requests

## Monitor

* Fetch requests
* AJAX calls

---

👉 Observe real API usage

---

# 🚨 High-Value Findings

* Hardcoded API keys
* Hidden endpoints
* Debug functions
* Role-based logic flaws

---

# 🧠 Pro Workflow

1. Collect JS files
2. Beautify code
3. Search keywords
4. Extract endpoints
5. Test them manually

---

# ⚠️ Key Insight

JavaScript reveals what developers tried to hide
