# 🛡️ Security Headers Checklist

> Quick checklist for analyzing HTTP security headers

---

## 🔍 Check These Headers

### Content-Security-Policy

* Is it present?
* Is it strict?

---

### X-Frame-Options

* DENY or SAMEORIGIN?

---

### X-Content-Type-Options

```http
nosniff
```

---

### HSTS

```http
Strict-Transport-Security
```

---

### Referrer-Policy

* no-referrer
* strict-origin

---

## 🚨 Common Issues

* Missing headers
* Weak CSP (`unsafe-inline`)
* No HSTS

---

## 🧠 Tools

* Browser DevTools
* Burp Suite
* securityheaders.com

---

## ⚠️ Insight

Headers reduce risk but don’t fix core vulnerabilities
