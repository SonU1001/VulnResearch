# Security Misconfiguration

---

## 📌 Description

Security Misconfiguration occurs when security settings are not properly defined, implemented, or maintained.

This includes default configurations, unnecessary features, exposed files, and improper permissions.

---

## ⚙️ How It Works (Technical)

Applications, servers, and frameworks come with default settings.

If these are not changed or hardened, attackers can exploit them.

Examples:

* Default credentials
* Debug mode enabled
* Directory listing enabled

---

## 💣 Common Examples

### Default Credentials

```plaintext
admin:admin
root:root
```

---

### Exposed Configuration Files

```url
https://example.com/.env
https://example.com/config.php
```

---

### Debug Mode Enabled

Error messages revealing:

* File paths
* Stack traces
* Internal logic

---

### Directory Listing

```url
https://example.com/uploads/
```

👉 Shows all uploaded files

---

## 📍 Common Places to Find

* Web servers
* Application frameworks
* Cloud storage (S3 buckets)
* Admin panels

---

## 🌍 Real-World Impact

* Sensitive data exposure
* Unauthorized access
* System compromise
* Information leakage

---

## 🔎 Detection Methodology (Pentester Approach)

1. Check for default credentials
2. Look for exposed files:

   * `.env`
   * `.git`
   * backup files
3. Trigger errors to see debug info
4. Test directory listing
5. Scan for unnecessary open services

---

## 🛡️ Remediation

* Disable default credentials
* Turn off debug mode in production
* Restrict access to sensitive files
* Remove unused services and features
* Apply proper permissions

---

## 🧠 Key Takeaway

Security Misconfiguration happens when systems are not properly secured, often due to human error or default settings.
