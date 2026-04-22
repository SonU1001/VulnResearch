# Broken Authentication

---

## 📌 Description

Broken Authentication refers to flaws in the authentication mechanisms that allow attackers to compromise passwords, session tokens, or user identities.

These vulnerabilities can lead to account takeover.

---

## ⚙️ How It Works (Technical)

Authentication systems rely on:

* User credentials (username/password)
* Session management (cookies/tokens)

If these are improperly implemented, attackers can exploit them.

---

## 💣 Common Attack Scenarios

### Weak Password Policies

* Short or predictable passwords
* No complexity requirements

---

### Credential Stuffing

Using leaked credentials from other breaches:

```plaintext id="w1r0fx"
username:password
admin:admin123
user:test123
```

---

### Session Fixation

Attacker sets a session ID before login and reuses it after victim logs in.

---

### Missing Rate Limiting

Unlimited login attempts → brute force attack

---

## 📍 Common Weak Points

* Login systems
* Password reset functionality
* Session cookies
* API authentication

---

## 🌍 Real-World Impact

* Account takeover
* Unauthorized access to sensitive data
* Privilege escalation
* Financial fraud

---

## 🔎 Detection Methodology (Pentester Approach)

1. Test login functionality:

   * Weak passwords
   * Default credentials
2. Attempt brute force (if no rate limiting)
3. Analyze session tokens:

   * Predictable?
   * Reusable?
4. Test password reset:

   * Token strength
   * Expiration
5. Check multi-factor authentication (MFA)

---

## 🛡️ Remediation

* Enforce strong password policies
* Implement rate limiting and CAPTCHA
* Use secure session management
* Enable multi-factor authentication (MFA)
* Store passwords securely (hashed + salted)

---

## 🧠 Key Takeaway

Broken Authentication allows attackers to bypass login mechanisms and gain unauthorized access to user accounts.
