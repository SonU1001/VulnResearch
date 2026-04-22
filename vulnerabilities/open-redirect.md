# Open Redirect

---

## 📌 Description

Open Redirect is a vulnerability where a web application allows users to be redirected to an external URL without proper validation.

Attackers can exploit this to redirect victims to malicious websites.

---

## ⚙️ How It Works (Technical)

Web applications often use a parameter to redirect users after login or certain actions.

Example:

```url
https://example.com/redirect?url=https://trusted.com
```

If the application does not validate the `url` parameter, an attacker can modify it:

```url
https://example.com/redirect?url=https://evil.com
```

👉 User gets redirected to a malicious site

---

## 💣 Example Payloads

### Basic Redirect

```url
https://example.com/redirect?url=https://attacker.com
```

---

### Bypass Using Encoded URL

```url
https://example.com/redirect?url=https%3A%2F%2Fattacker.com
```

---

### Using @ Trick

```url
https://example.com/redirect?url=https://trusted.com@attacker.com
```

👉 Browser interprets it as attacker.com

---

## 📍 Common Places to Find

* Login redirect pages
* Password reset links
* Logout pages
* Third-party integrations

---

## 🌍 Real-World Impact

* Phishing attacks
* Credential theft
* Bypass of security filters
* Chaining with other vulnerabilities

---

## 🔎 Detection Methodology (Pentester Approach)

1. Identify redirect parameters:

   * `url=`
   * `redirect=`
   * `next=`
2. Replace value with external domain
3. Observe behavior:

   * Does it redirect?
4. Try bypass techniques:

   * URL encoding
   * Double encoding
   * Using `@` symbol

---

## 🛡️ Remediation

* Validate and whitelist allowed domains
* Avoid using user-controlled input for redirects
* Use relative paths instead of full URLs

---

## 🧠 Key Takeaway

Open Redirect may seem low severity, but it is powerful when combined with phishing or other attacks.
