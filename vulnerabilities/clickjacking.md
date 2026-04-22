# Clickjacking

---

## 📌 Description

Clickjacking is a vulnerability where a user is tricked into clicking on something different from what they perceive, potentially performing unintended actions.

This is typically done by embedding a website inside an invisible iframe.

---

## ⚙️ How It Works (Technical)

An attacker loads the target website inside an iframe and overlays it with deceptive content.

Example:

```html id="d2k9pz"
<iframe src="https://example.com" style="opacity:0; position:absolute;"></iframe>
<button>Click here to win a prize!</button>
```

👉 User clicks the button but actually interacts with the hidden iframe

---

## 💣 Example Attack Scenarios

* Like/Follow buttons on social media
* Changing account settings
* Initiating financial transactions
* Granting permissions

---

## 📍 Common Targets

* Banking websites
* Admin panels
* Social media platforms
* Account settings pages

---

## 🌍 Real-World Impact

* Unauthorized actions
* Account compromise
* Privacy violations

---

## 🔎 Detection Methodology (Pentester Approach)

1. Try loading the target site inside an iframe:

   ```html
   <iframe src="https://target.com"></iframe>
   ```
2. Check if it loads successfully
3. If yes → likely vulnerable
4. Try overlaying elements to simulate attack

---

## 🛡️ Remediation

* Use `X-Frame-Options` header:

  * DENY
  * SAMEORIGIN
* Use Content Security Policy (CSP):

  ```http
  Content-Security-Policy: frame-ancestors 'none';
  ```
* Avoid allowing embedding from untrusted domains

---

## 🧠 Key Takeaway

Clickjacking tricks users into performing actions by hiding the real interface behind deceptive elements.
