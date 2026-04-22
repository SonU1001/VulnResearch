# HTTP Security Headers Misconfiguration

---

## 📌 Description

HTTP Security Headers are used by web applications to instruct browsers on how to behave securely.

Misconfiguration or absence of these headers can expose applications to various attacks.

---

## ⚙️ How It Works (Technical)

Web servers send headers in HTTP responses that control browser behavior.

Example:

```http id="r4j9lm"
X-Frame-Options: DENY
```

These headers help mitigate vulnerabilities like XSS, clickjacking, and data injection.

---

## 💣 Important Security Headers

### 1. Content-Security-Policy (CSP)

Controls which resources can be loaded:

```http id="g0z6vr"
Content-Security-Policy: default-src 'self'
```

---

### 2. X-Frame-Options

Prevents clickjacking:

```http id="lj1k0w"
X-Frame-Options: DENY
```

---

### 3. X-Content-Type-Options

Prevents MIME-type sniffing:

```http id="u5o7l2"
X-Content-Type-Options: nosniff
```

---

### 4. Strict-Transport-Security (HSTS)

Forces HTTPS:

```http id="b8z2hn"
Strict-Transport-Security: max-age=31536000; includeSubDomains
```

---

### 5. Referrer-Policy

Controls referrer information:

```http id="j2r8qv"
Referrer-Policy: no-referrer
```

---

## 📍 Common Issues

* Missing headers
* Weak CSP policies
* Misconfigured HSTS
* Allowing unsafe inline scripts

---

## 🌍 Real-World Impact

* XSS attacks become easier
* Clickjacking becomes possible
* Data leakage through headers
* Reduced overall security posture

---

## 🔎 Detection Methodology (Pentester Approach)

1. Inspect HTTP response headers (Burp Suite / browser dev tools)
2. Check for missing headers
3. Analyze CSP strength
4. Use tools like securityheaders.com
5. Identify misconfigurations

---

## 🛡️ Remediation

* Implement all recommended security headers
* Use strict CSP policies
* Regularly audit header configurations
* Follow best practices (OWASP guidelines)

---

## 🧠 Key Takeaway

Security headers act as an additional layer of defense by guiding browser behavior and preventing common attacks.
