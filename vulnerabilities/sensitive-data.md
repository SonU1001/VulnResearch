# Sensitive Data Exposure

---

## 📌 Description

Sensitive Data Exposure occurs when an application fails to properly protect sensitive information such as passwords, personal data, or financial details.

This can happen due to weak encryption, improper storage, or insecure transmission.

---

## ⚙️ How It Works (Technical)

Sensitive data should be:

* Encrypted during transmission (HTTPS)
* Encrypted at rest
* Properly access-controlled

If not, attackers can intercept or access it.

---

## 💣 Common Examples

### Data Sent Over HTTP

```http id="s5m2vk"
http://example.com/login
```

👉 Data can be intercepted (Man-in-the-Middle attack)

---

### Weak or No Encryption

* Passwords stored in plain text
* Use of weak hashing algorithms (MD5, SHA1)

---

### Exposed API Responses

```json id="jq2a91"
{
  "username": "user1",
  "password": "123456"
}
```

---

### Sensitive Files Publicly Accessible

```url id="z52y0p"
https://example.com/backup.zip
https://example.com/database.sql
```

---

## 📍 Common Places to Find

* Login and registration systems
* API responses
* Backup files
* Cloud storage
* Database dumps

---

## 🌍 Real-World Impact

* Identity theft
* Financial fraud
* Privacy violations
* Large-scale data breaches

---

## 🔎 Detection Methodology (Pentester Approach)

1. Check if site uses HTTPS
2. Inspect network traffic (Burp Suite)
3. Look for sensitive data in responses
4. Test for exposed files:

   * backups
   * logs
5. Analyze password storage (if possible)

---

## 🛡️ Remediation

* Use HTTPS everywhere
* Encrypt sensitive data
* Store passwords securely (bcrypt, Argon2)
* Avoid exposing sensitive data in responses
* Apply proper access controls

---

## 🧠 Key Takeaway

Sensitive Data Exposure occurs when applications fail to properly protect confidential information, making it accessible to attackers.
