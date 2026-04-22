# Cross-Site Request Forgery (CSRF)

---

## 📌 Description

Cross-Site Request Forgery (CSRF) is a vulnerability that tricks a victim into performing unwanted actions on a web application where they are authenticated.

The attack exploits the trust that a website has in the user's browser.

---

## ⚙️ How It Works (Technical)

When a user is logged into a website, their browser automatically includes authentication data (such as cookies) in every request.

If a malicious request is sent from another site, the browser will still include these credentials.

Example:

```http
POST /change-password HTTP/1.1
Host: example.com
Cookie: session=abcd1234
```

If no protection exists, an attacker can trigger this request without the user knowing.

---

## 💣 Example Attack

### Malicious HTML

```html
<form action="https://example.com/change-email" method="POST">
  <input type="hidden" name="email" value="attacker@email.com">
</form>

<script>
document.forms[0].submit();
</script>
```

👉 If victim is logged in → email gets changed

---

## 📍 Common Targets

* Change password
* Change email
* Money transfer
* Account settings
* Admin actions

---

## 🌍 Real-World Impact

* Account takeover
* Unauthorized transactions
* Data modification
* Privilege abuse

---

## 🔎 Detection Methodology (Pentester Approach)

1. Identify sensitive actions (POST/GET requests)
2. Capture request using proxy (like Burp Suite)
3. Check for CSRF token:

   * If missing → vulnerable
4. Remove token and replay request
5. Create PoC (HTML form) to reproduce attack

---

## 🛡️ Remediation

* Implement CSRF tokens (random, unique per session)
* Use SameSite cookie attribute
* Require re-authentication for sensitive actions
* Validate origin and referer headers

---

## 🧠 Key Takeaway

CSRF works because browsers automatically send authentication data, allowing attackers to perform actions without user consent.
