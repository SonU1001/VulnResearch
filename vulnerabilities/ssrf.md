# Server-Side Request Forgery (SSRF)

---

## 📌 Description

SSRF is a vulnerability that allows an attacker to make the server send HTTP requests to unintended locations.

This can be used to access internal systems, cloud metadata, or restricted services.

---

## ⚙️ How It Works (Technical)

Applications sometimes fetch data from user-supplied URLs.

Example:

```url id="shm3ok"
https://example.com/fetch?url=http://api.partner.com/data
```

If not validated, attacker can change it:

```url id="l79d7t"
https://example.com/fetch?url=http://localhost/admin
```

👉 Server makes request to internal service

---

## 💣 Example Payloads

### Access Internal Services

```url id="q6lhvc"
http://127.0.0.1:8080
```

---

### Access Cloud Metadata (AWS)

```url id="6ksp17"
http://169.254.169.254/latest/meta-data/
```

👉 Can expose credentials

---

### File Access

```url id="0h3fcw"
file:///etc/passwd
```

---

## 📍 Common Places to Find

* URL preview features
* Image upload via URL
* Webhooks
* API integrations
* PDF generators

---

## 🌍 Real-World Impact

* Internal network scanning
* Access to admin panels
* Cloud credential leakage
* Remote code execution (in some cases)

---

## 🔎 Detection Methodology (Pentester Approach)

1. Identify features that accept URLs
2. Provide external URL (Burp Collaborator or webhook)
3. Check if server makes request
4. Try internal addresses:

   * 127.0.0.1
   * localhost
   * internal IP ranges
5. Test cloud metadata endpoints

---

## 🛡️ Remediation

* Validate and whitelist allowed domains
* Block internal IP ranges
* Disable unnecessary URL fetching
* Use network-level protections (firewalls)

---

## 🧠 Key Takeaway

SSRF allows attackers to use the server as a proxy to access internal or restricted resources.
