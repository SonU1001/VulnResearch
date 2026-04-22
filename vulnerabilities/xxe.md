# XML External Entity (XXE)

---

## 📌 Description

XXE is a vulnerability that occurs when an application processes XML input without properly disabling external entity references.

It allows attackers to read local files, perform SSRF, or cause denial of service.

---

## ⚙️ How It Works (Technical)

XML allows defining entities that can reference external resources.

Example:

```xml id="cb9u2f"
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
```

If the parser processes this entity, it will include the file content in the response.

---

## 💣 Example Payload

```xml id="6m8v9d"
<?xml version="1.0"?>
<!DOCTYPE data [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<data>&xxe;</data>
```

👉 Server returns contents of `/etc/passwd`

---

## 📍 Common Places to Find

* File upload features (XML)
* SOAP APIs
* SAML authentication
* XML-based web services

---

## 🌍 Real-World Impact

* Sensitive file disclosure
* Server-side request forgery (SSRF)
* Denial of Service (Billion Laughs attack)
* Internal system access

---

## 🔎 Detection Methodology (Pentester Approach)

1. Identify XML input endpoints
2. Submit basic XML
3. Inject external entity payload
4. Observe response:

   * Does it return file content?
5. Test SSRF using external URLs

---

## 🛡️ Remediation

* Disable external entity processing in XML parsers
* Use secure libraries
* Validate and sanitize XML input
* Prefer JSON over XML when possible

---

## 🧠 Key Takeaway

XXE occurs when XML parsers process external entities, allowing attackers to access internal or sensitive resources.
